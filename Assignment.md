### 1. 본인이 작성했던 코드 중 공유하고 싶은 코드를 이유와 함께 마크다운 code block 을 사용해 올려주세요
* 언어 상관없음
* 어떤 로직이든 상관없음
* 단, 길이가 길지 않은 함수 단위가 좋습니다

```
private static int[] solution(int[] array, int[][] commands) {
    int[] answer = new int[commands.length];
    int[] real = array;
    int i=0;

    for(int[] arr : commands){
        array = Arrays.copyOfRange(array, arr[0]-1, arr[1]);
        Arrays.sort(array);
        answer[i] = array[arr[2]-1];
        i++;
        array = real;
    }
    return answer;
}
```
+ 최근 코딩테스트를 하면서 copyOfRange를 사용하는 방법을 공부했는데 새로 알게 된 개념이라 공유합니다.

### 2. Layered Architecture(계층 아키텍처)에 대해서 설명해 주세요
+ 소프르웨어 시스템을 분리하는 방법의 하나로 계층의 아래에 해당하는 요소에 의존하는 아키텍처이다. 
+ 일반적으로 4계층으로 이뤄져 있으며, Presentation / Business / Persistence / Database Layer로 나뉜다.
+ Presentation Layer : 시스템을 사용하는 사용자와의 상호작용을 처리, MVC단
+ Business Layer : 서비스 핵심 로직으로 유효성 검사, 계산 등을 수항하는 논리 계층이다.
+ Persistence Layer : DAO 계층. DB, 외부 API 통신을 처리하는 계층이다.

### 3. Dependency Injection(의존성 주입)의 개념과 함께, 왜 필요한지 작성해 주세요
+ 클래스 간 의존성을 외부에서 주입하는 것.
+ 클래스 간 의존 관계를 생성하게 되는데, 객체 지향적인 설계가 가능하게 한다.
+ 의존성 주입으로 클래스간 결합도가 약해지게 되는데, 이 경우 하나의 수정으로 리펙토링을 수월하게 하고, 확장성을 높이는데에 있다.

### 4. 본인이 사용하는 언어의 Functional Programming(함수형 프로그래밍) 스펙을 예제와 함께 소개해 주세요
+ java
+ collection, steam를 이용하거나 람다를 이용한 간결한 표현방식을 선호합니다.
```java
Optional<MaintenanceSub> maintenancesub = GetSubCategory(name);
if(maintenancesub.isEmpty()){
    return this.SubCategorys.stream().filter(f -> f.getList().contains(name)).count() > 0;
}else{
    return SubCategorys.contains(maintenancesub.get());
}
```

### 5. (코드 작성) 다음 스펙을 만족하는 delay 함수를 작성해 주세요 (hint: Promise 사용)
```ts
    type SomeFunctionReturnString = () => string

    function delay(f: SomeFunctionReturnString, seconds: number): Promise<string> {
        return new Promise<string>((resolve, reject) => {
          setTimeout( () => {
            try{
              const msg = f();
              return resolve(msg);
            } catch (e) {
              reject(e);
            }
          } , seconds);
        })
    };

    const success = () => {
      return "successfully done";
    };

    const fail = () => {
      throw new Error("failed");
    };

    delay(success, 2) // 2초 뒤에 successfully done 로그
      .then((res) => console.log(res))
      .catch((e) => console.log(e));

    delay(fail, 2) // 2초 뒤에 failed 로그
      .then((res) => console.log(res))
      .catch((e) => console.log(e));
```
**결과값**
```
    $ ts-node delay.ts
    successfully done
    Error: failed
```

### 6. 강의를 통해서 기대하는 바, 또는 얻고 싶은 팁을 적어주세요
+ 강의에서 제공하는 언어를 사용해보지 않았는데 이번 기회에 스케줄에 맞춰 학습하고 이해도를 높이고 싶습니다.
