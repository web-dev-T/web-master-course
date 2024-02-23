##### Selector를 만드는 방법이 뭔가요?
사람을 부를 때도 이름으로 부를 수도 있고, 외형으로 부를 수도 있고, 별명으로 부를 수도 있죠? 요소를 가리킬 때도 다양한 방법으로 가리킬 수 있습니다. 그 다양한 방법에 대해 배워봅니다.

> 🗣️: 거기 키 크고 빨간 안경 쓰신 남성 분 옆에 여성 분!

##### 주요(자주 사용하는) Selector Pattern
- `*` : 모든 요소
```html
<style>
  * {
    font-weight: bold;
  }
</style>

<div> hello </div>
```
- `E` : E라는 이름의 특정 태그 
```html
<style>
  div {
    font-weight: bold;
  }
</style>

<div> hello </div>
```
- `.C`: C라는 class 속성 값을 갖는 태그 - html [[class attributes]]
```html
<style>
  .greeting {
    font-weight: bold;
  }
</style>

<div class="greeting"> hello </div>
```
- `E.C` : E라는 이름의 특정 태그 중 class 속성이 C라는 값을 갖는 태그
```html
<style>
  div.greeting {
    font-weight: bold;
  }
</style>

<div class="greeting"> hello </div>
```
- `E#I`: E라는 이름의 특정 태그 중 id 속성이 I라는 값을 갖는 태그
```html
<style>
  #hello {
	 font-weight: bold;
  }
</style>

<div id="greeting"> hello </div>
```
- `E[foo]` : E라는 태그 중 foo라는 속성을 갖는 태그
```html
<style>
  a[href] {
    color: green;
  }
</style>
<a href="https://www.naver.com">네이버</div>
```
- `E[foo="bar"]` : E라는 태그 중 foo 속성이 bar라는 값을 갖는 태그
```html
<style>
  a[href="https://www.naver.com"] {
    color: green;
  }
</style>
<a href="https://www.naver.com">네이버</div>
```
- `E:nth-child(n)`: E라는 이름의 특정 태그 중  n번째 자식인 경우
```html
<style>
  p:nth-chile(1) {
    color: red;
  }
</style>
<div>
  <p>red paragraph</p> <!-- 이 요소를 가리키게 됩니다. -->
  <p>paragraph</p>
  <p>paragraph</p>
</div>
```
- `E:first-child` : E라는 이름의 특정 태그 중  1번째 자식인 경우
- `E:last-child` : E라는 이름의 특정 태그 중  마지막 자식인 경우
- `E F` : E라는 이름의 특정 태그가 조상에 있는 F라는 이름의 태그
- `E > F` : E라는 이름의 특정 태그를 부모로 갖는 F라는 이름의 태그
```html
<style>
.box1 > .box2 {
  color: blue;
}
.box1 .box3 {
  color: red;
}
</style>
<div class="box1">
  <div class="box2">
    blue text 
    <div class="box3"> red text </div>
  </div>
</div>
```
- `E + F` : E라는 요소를 직전 형제로 갖는 F 요소
- `E ~ F` : E라는 요소를 형제로 갖는 뒤 따르는 F 요소
```html
<style>
.box1 + .box2 {
  color: blue;
}
.box1 ~ .box3 {
  color: red;
}
</style>
<div>
  <div class="box1"></div>
  <div class="box2">blue text</div>
  <div class="box3">red text</div>
</div>
```

##### Pseudo Selector
Pseudo code의 의미와 유사하게 가짜 Selector, 가상의 Selector라는 것이 있습니다.
pseudo class와 psuedo element 2가지가 있는데요. 

pseudo selector가 존재하여 불필요한 class(html 태그의 attributes)를 짓는 것을 줄일 수 있습니다. 

- pseudo class -  `selector:state`
주로 어떤 상태를 나타날 때 많이 쓰입니다. 웹 서핑을 하다보면 특정 위치에 마우스를 올렸을 때 색상이 바뀌거나 크기가 커지는 등의 효과를 본 적이 있으실 겁니다. 이러한 것을 구현할 때 사용하는데요. `selector:state` 의 문법으로 사용됩니다. [더 알아보기](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)

```html
<style>
  .box {
    width: 100px;
    height: 100px;
    background-color: red;
  }

  .box:hover {
    background-color: blue;
  }
</style>
<div class="box"></div>
```

- pseudo element - `selector::pseudo-element`
주로 요소의 특정 위치 등을 나타내거나 가상의 요소를 가리킬 때 사용됩니다. 예를 들어 paragraph의 첫 줄을 가리키거나 첫 문자 등을 가리키는데 사용될 수 있습니다. [더 알아보기](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)

```html
<style>
  p::first-letter {
    font-weight: bold;
  }
  
  p::first-line {
    color: red;
  }
</style>
<p style="width: 100px;">
  안녕하세요 반갑습니다.
</p>
```

##### Selector list
여러 selector 들이 동일한 rule set을 가질 경우 selector list를 이용할 수 있습니다.

```css
h1 {
  color: blue;
}

.special {
  color: blue;
}
```

```css
h1,
.special {
  color: blue;
}
```

위 두 CSS는 결과적으로 동일한 효과를 갖습니다.