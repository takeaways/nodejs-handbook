# NodeJs Handbook with Jsor

## I/O
- 컴퓨터는 데이터를 입력 받고, 출력하기 위한 것이다.
- 네트워크 요청에 대한 응답 

## 비동기 vs 동기
- 동기화는 요청에 대한 응답이 완료되기 까지 기다리는행위 
- 노드는 비동기로 동작되기 때문에 완료를 기다리지 않는다.
- v8엔진에 의한 event loop를 사용한다. (이벤트 주도)

## Non-blocking vs Blocking
- 자바스크립트 언어의 특정이 non-blocking 입니다.
- 작업의 완료를 기다리지 않는다.

## Front-End vs Back-End 차이점
- window vs global
- module system
    - require("react") 구문을 사용할 수 있다.
    - import react from "react": 별도의 셋팅이 필요합니다.
- let, const식 (블록 단위 스코프) > var (파일 내부 전역적으로 인)

## REPL
- 실시간으로 코드를 사용할 수 있습니다.
- powershell node

## npm (Node Package Manager)
- npm -v (--version)
- node -v (--version)
- npm 명령어지 모음
    ```bash
    # npm init음 
    # npm i  package's name // 설치
    # npm uninstall package's name // 제거 
    # npm update // package-lock.json 의존성 생겨버림
    # npm i -g package's name치 // 글로벌 설치
    # npx create-react-app //실행 자체를 목적으로 하는 패키
  ```
 ## Semantic versioning
 - 3 자리로 표현된 버전
 - First release : 1.0.0
 - Backward compatible bug fixes : 1.0.1
 - Backward compatible new features : 1.1.0
 - Changes that break backword compatibility : 2.0.0
 - ~ Patch release
 - ^ Minor release
 - \* Major release
 
 ## npx 
 - 명령의 실행을 목적으로 한다.
 - npx cowsay "Hello World"
 
 ## nodemon
 - 사용의 목적
    - auto save : 파일의 변화를 감지하여 재실행 시켜준다.
     ```bash
     # npm i -g nodemon 
    ```

## module.exports
- 파일을 모듈로 만드는 방법
- 단일 파일로 config 파일로 엮어서 표현할 수 있다.
    ```code
    function edit() {}
    function add() {}
    module.exports = {
        edit,
        add,
        id,
        fn: () => {}
    } 
    ```
  
## Event Loop [1]
 - Que : FIFO (First In First Out)
     ```javascript
   'use strict' // typesciprt를 사용합니다.
    const queue = [];
    queue.push(1);
    queue.push(2);
    const result = queue.shift() // 1 : 첫 번째 요소를 제거하고 리턴한다.
    ```
  - Stack : LIFO (Last In First Out)
      ```javascript
    'use strict' // typesciprt를 사용합니다.
     const stack = [];
     stack.push(1);
     stack.push(2);
     const result = queue.pop() // 2 : 마지막 요소를 제거하고 리턴한다.
     ```
 ## Event Loop [2]
 - Call Stack
 - Callback Queue
 - Event Loop
 
 ## API
 ### 1. every
 - 배열이 모든 조건을 만족할 경우에 리턴.
    ```typescript
   'use strict' // typesciprt를 사용합니다.
    const arr:number[] = [2,3,4];
    const isBiggerThenOne:boolean = arr.every(element => element > 1)
    ```
### 2. find, includes
 - 배열에 포함 되어 있는가 그러면 리턴해
 - 포함되어 있는지 boolean 값을 리턴한다. //메로리의 누수를 만들 수 방지한다.
### 3. forEach
 - 직관적으로 코드를 확인할 수 있다.
 - 내부 실행 함수는 비동기 적으로 실행되기 때문에 주의해서 사용해야 합니다.
    ```typescript
    const arr:number[] = [1,2,3];
    arr.forEach(item => {console.log(item)});
    ```
### 4. map, filter
  - 결과를 배열로 반환한다.
  - map : 리턴하는 값으로 새로운 배열을 리턴한다.
  - filter : 조건을 만족하는 배열의 요소만 반환하는 새로운 배열을 반환된다.
### 5. object.assign, spread
  - 새로운 객체를 만들거나, 다른 객체를 합쳐 새로운 객체를 만든다.
      ```typescript
      const obj1 = {};
      const obj2 = {};
      const arr1 = [];
      const arr2 = [];
      const newObj = Object.assign(obj1, obj2); // {...obj1, ...obj2}
      const newArray = [...arr1, ...arr2];
      ```
### 6. Set
  - 중복을 제거한 자료형
      ```javascript
    'use strict'
      const test = new Set();
      test.add(1);
      test.add(2);
      test.add(3);
      test.add(1);
      for(const item of test){}
      const r = test.has(3); // true
      console.log(test) // [1,2,3]
      ```
### 7. some
  - 최초 한 개 이상의 조건이 만족하는
      ```javascript
      'use strict'
      const arr = [0, -1, -2, 1, 40,4]
      arr.some(item => item < 0) // true
      ```
### 8. Template String
 - 변수와 스트링을 쉽게 다룰 수 있다.
      ```javascript
   'use strict'
       `(Back quart)
           ${변수}님 만나서 반가워요
       ` 
      ```
### String
 - 문자열 기능을 포함한다.
    ```javascript
    'use strict' 
    let string = "nodejs is"
    let isStartWith = string.starwith("n"); // true
    let isIncludes = string.includes('js'); // true
    let isEndWith = string.endWith('s'); // true
    ```
 ### Type Checking
  - typeof
    ```javascript
    const string = "node.js"; // typeof string - string 
    const array = []; // typeof array - object
    const obj = {}; // typeof obj - object
    const number = 1; // typeof number - number
    ```
 ## 호이스팅
  - 자바스크립트에 생성및 실행 단계가 어떻게 동작하는 가에대한 일반 적인 생각
  - 변수 및 함수 선언은 컴파일 단계에서 메모리에 저장 되지만 코드 구문을 실행 하기전에
  - 함수선언을 메모리에 저장하는 특징 
  - 
 ## 즉시 실행함수 IIFE
  - 함수를 선언하자 마자 사용
  - 전역 스코프에 불필요한 변수를 추가해서 오염시키는 것을 방지할 수 있다.
    ```javascript
    (function() {
      var lang = "hello"
    })();
    console.log(lang) // 내부의 변수로 접근 불가능
    ```
## setInterval
 - 특정 시간마다 코드를 시작하게 할 수 있다.
      ```javascript
      setInterval(()=>{
        console.log("hello") // 1초마다 실행된다.
      },1*1000);
      ```
## Error Handling
 - 오류에 대한 코드 처리
    ```javascript
    try{
     a
     console.log(a); // Error 발생;
    }catch (e) {
       console.error(e) 에러 처리
    }
    console.log('a')  //에러 처리된 다음 실행
    ```
   
## Arrow Function
 - () => {} 
 - this의 근본적인 문제를 해결한다.
    ```javascript
    function add(a,b){return a +b;}
    const add = (a,b) => a+b; 
    ```
 - curried function : 합성함수 파라미터를 반복적으로 받는 행위를 줄일 수 있다.
   ```javascript
   'use strict'
   //1. 회원들에게 혜택을 주어야 한다. 고객의 등급을 어떻게 처리 할 것인가?
   function getDiscoout(price, rate){
       return price * rate;
   }
   getDiscoout(10000, 0.5);
   //2. 위의 함수를 arrow평션을 이용한다. queried 
   const getDiscount2 = (price, rate) => price * rate;
   getDicount2(1000,0.2);
   
   const tenpercentOff = rate => price => rate * price;
   const getDiscount = tenpersontOff(0.1);
   getDiscount(1000) // 100;
   ```   
# [2] Class
1. OOP 개념을 쉽게 사용할 수 있도록 만들어진 Sugar Syntax
2. ES2015 = ES6 입니다.
3. 데이터 베이스 매니져, 캐쉬 데이터 매니저를 사용할 때 아주 도움이 됩니다. !!
4. 필요한 이유는?
    - 환경설정 파일을 구성할 때 사용하는 것이 가장 크다.
    - 동일한 환경 변수를 읽는 행위가 많아 지면 낭비다.
    - 사용자는 5초 이상 페이지를 기다리지 않는다.
    - 싱글톤 패턴과 클래스를 생성하면 한 번만 생성된다. - 불필요한 작업을 생략할 수 있다.
    ```javascript
    'use strict'
    // 중복되는 SQL을 다시 작성하지 않도록할 수 있다.
    class CacheManager{
          constructor() { //async 사용할 수 없으며, 동기화된 코드로만 작성해야 합니다.
               this.config = []          
          }
    }
   
    const cacheManager = new CacheManager();
    ```
