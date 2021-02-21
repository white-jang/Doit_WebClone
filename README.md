<h1>Doit_WebClone</h1>
<br/>  
  
# 💌소개 
`Do it! Web clone 웹 사이트 따라 만들기`를 따라 완성한 웹 사이트 예제입니다.  
  
# 🛠기술 스택  
✔HTML, CSS, JQuery를 활용하여 제작  
✔구글 앱스 메일 API를 활용하여 문의 메일 처리  
✔Ajax를 활용하여 책 소개 페이지 구성  
<br/>  

# 💾챕터별 정리

# 1 Chap

**🔹1. HTML 지식🔹**  
각 브라우저에는 엔진이 있으며, 엔진들은 브라우저 엔진과 렌더링 엔진으로 구분된다.  
렌더링 엔진이 HTML을 해석하고 CSS에 정의된 스타일로 화면에 배치한다.

```
랜더링 엔진 동작 과정
1. HTML 작성 순서대로 트리 생성 ➡ 2. CSS 처리 ➡ 3. 랜더 트리 생성 ➡ 4. 랜더 트리를 적용된 스타일대로 배치
```

브라우저 엔진 종류로는 **Webkit(구글, 사파리), Gecko(파이어폭스), Blink(오페라)** 가 있다.  
웹 크롤러(Web crawler)는 HTML 태그를 기반으로 웹 페이지의 콘텐츠 내용을 확인한다.  
따라서, **검색 엔진 최적화(Search Engine Optimiztion, SEO)** 가 중요하다.  
검색 엔진 최적화를 위해서는 콘텐츠의 구조와 의미까지 구분하여 HTML을 작성해야 한다.  
HTML을 단순히 화면에 콘텐츠를 표시하여 보이게 하는 것이 아니라,  
**❗웹 크롤러가 HTML의 구조와 내용을 명확하게 파악할 수 있도록 작성할 것❗**

**🔹2. meta 태그🔹**  
**웹 크롤러가 HTML 문서에 방문할 때, 웹 사이트는 meta 태그에 지정한 요약 내용을 알려준다.**  
2019년 7월 기준으로 구글 웹 크롤러는 \<meta\> 태그의 keyword 속성을 수집하지 않는다고 했다.  
이렇게 웹 크롤러의 검색 기준은 변경될 수 있으므로,  
공식 가이드에 맞춰 작성하는 것이 검색 엔진 최적화에 가장 좋은 방법이다.  
meta 태그는 기본적으로 빈 요소이기 때문에 시작 태그만 존재한다. _(닫는 태그가 없다.)_

- name="format-detection"
  - 모바일로 웹 페이지를 사용할 때 기본적으로 제공하는 것에 대한 설정
  - ex) 모바일에서 숫자 선택하면 전화 연결되는 경우
- property="og:…"
  - 오픈 그래프(Open Graph, OG) 설정
  - 오픈 그래프는 웹 페이지가 소셜 미디어로 공유될 때 표시되는 카드 형식
  - 카카오톡, 페이스북 등 SNS에서 사용함

```
<meta http-equiv="X-UA-Compatible" content="IE=edge">  // 호환성 보기 기능 활성화
<meta name="viewport" content="width=device-width, initial-scale=1.0">
// 화면에 보이는 영역(viewport)의 너비를 현재 기기의 width로 정하고, 초기 화면 배율을 1로 지정

<meta name="title" property="og:title" content="이지스퍼블리싱">
<meta name="images" property="og:image" content="./images/link_thumb.jpg">
<meta name="description" property="og:description" content="Do it! 웹 사이트 하나 만들고 웹 퍼블리셔 되기">
// 오픈 그래프 내용
```

# 2 Chap

**🔹1. 크로스 브라우징이란?🔹**  
사용자가 어느 기기나 브라우저에서 웹 사이트에 접속해도 불편함 없이 웹 사이트를 사용하도록  
**웹 표준을 지켜 만드는 방법론적 가이드**를 의미한다.  
즉, 코드 호환성을 지키는 것이 중요하며 코드 호환성은 Can I Use(www.caniuse.com)에서 간단히 확인할 수 있다.  
_flex의 경우, IE11부터 적용됨을 알 수 있음._

**🔹2. 벤더 프리픽스란?🔹**  
CSS3의 경우 권고 안에는 포함되어 있지만, 아직 완벽한 상태가 아닌 기능들이 있다.  
각 브라우저에서 실험적으로 이런 완벽하지 않은 CSS 코드를 제공하기 위해 벤더 프리픽스(접두어)를 사용한다.  
즉, **벤더 프리픽스는 브라우저 개발사가 실험적으로 CSS의 속성을 사용할 수 있도록 제공하는 기능**

```
CSS 벤더 프리픽스(접두어)의 예시 (border-radius)
**-webkit-**border-radius: 10px; | 사파리, 크롬
**-moz-**border-radius: 10px; | 파이어폭스
**-o-**border-radius: 10px; | 오페라
**-ms-**border-radius: 10px; | 인터넷 익스플로러
```

# 3 Chap

**🔹1. 통일성 있는 레이아웃이 중요!🔹**  
'레이아웃을 구성한다' == '정보를 잘 정리하여 일관된 모습으로 배치하는 것'  
페이지의 통일성을 맞추어 HTML을 작성해야 사용자 친화적인 구성이 가능하다.

**🔹2. 시맨틱 마크업은? (Semantic HTML)🔹**  
시맨틱 HTML은 각 태그를 문서의 의미에 맞게 작성하는 것이다.  
브라우저 기준으로 생각하면, 브라우저는 문서를 읽고 사용자의 화면에 정보를 보여주는 것이다.  
또한, 문서 내용과 구조의 의미를 태그를 통해 해석하고 정보를 받아들이게 한다.  
**즉, 시맨틱한 마크업으로 작성된 문서일 때 브라우저는 비로소 정확하게 정보를 해석할 수 있다.**  
참고할만한 사이트 https://yeoninim.tistory.com/20

**🔹3. CSS 선택자의 이해🔹**  
정리가 아주 잘 되어있는 사이트 http://www.nextree.co.kr/p8468/

# 4 Chap

**🔹1. CSS 적용 우선순위🔹**  
① 속성값 뒤에 !important를 붙인 속성  
② HTML에서 style을 직접 지정한 속성 (인라인)  
③ #id로 지정한 속성  
④ .클래스, :추상클래스로 지정한 속성  
⑤ 태그 이름으로 지정한 속성  
⑥ 상위 객체에 의해 상속된 속성

**🔹2. data- 속성🔹**  
특정 요소와 연관되어 있지 않지만 데이터에 대한 확장 가능성을 두고  
의미론적으로 HTML 요소에 추가 정보를 저장할 수 있는 속성이다.  
참고 자료 사이트 https://dololak.tistory.com/364

```
<input type="text" data-value="001"  data-code="c03"  id="username">
```

# 5 Chap

**🔹1. 효과적인 컨텐츠란?🔹**  
① CSS로 중요 정보에 미적인 요소를 가미해 사용자가 흥미를 느끼게 만든 것.  
② HTML로 브라우저뿐만 아니라 사용자에게도 정보르 논리적으로 제공.  
③ 작성된 내용이 다양한 브라우저에서도 잘 보이는지.

**🔹2. CSS 고도화🔹**  
완성된 페이지들의 통일성을 맞추거나 애니메이션의 퀄리티를 높이기 위해  
CSS를 재작성하거나 수정하는 일

# 6 Chap

**🔹1. float 속성🔹**  
float 속성은 사용 후 반드시 해제해야 한다.  
해제할 때는 overflow, clear 속성을 이용할 수도 있지만, 책에서는 가상 요소를 사용하여 해제했다.  
실무에서는 가상 요소를 사용하여 해제하는 것이 일반적이라고 한다.

```
.detail_content::after {
    content: "";
    display: block;
    clear: both;
}
```

**🔹2. \<em\>태그🔹**  
텍스트 내용을 강조할 때 사용하는 태그.  
strong, b, em, i 등의 태그를 분리해서 사용해야 웹 표준을 지킬 수 있다.  
관련해서 찾은 참고하기 좋은 사이트들:  
\<em\>vs\<strong\> : http://www.tcpschool.com/html-tags/em  
\<strong\>, \<em\>, \<b\>, \<i\>를 구분해서 사용하자! : https://blog.acronym.co.kr/358

**🔹3. 자주 사용하는 스타일은 CSS로 만들어 사용하자🔹**  
컨텐츠 전반에 비슷한 디자인이 있을 경우 추가로 CSS를 만들지 않고 공통으로 사용하도록 한다.  
만일 컨텐츠의 스타일이 달라지는 경우 기존의 공통 클래스를 기준으로 새로 스타일을 추가하여  
2개 클래스의 교집합으로 최종 스타일이 적용될 수 있도록 작성한다.

# 8 Chap

**🔹1. 사용자 인터페이스(UI)란?🔹**  
사용자와 시스템이 정보를 주고받기 위해 상호작용을 하는 의사소통 시스템.  
사용자와 도구 혹은 시스템 사이에서 상호작용을 하며 반응하는 방법을 UI라고 부른다.  
사용자를 자신의 사이트에 머물도록 하기 위해서는 사용자에게 제공하는  
인터페이스가 얼마나 사용자의 편의성을 고려했는지에 달려있다.

**🔹2. 좋은 웹 사이트란?🔹**  
시스템에 대한 배려와 사람에 대한 배려가 동시에 이루어진 웹 사이트.  
즉, 시맨틱 마크업과 사용자 편의성의 조화가 필요하다.

**🔹3. 좋은 UI를 만들기 위해 고려해야 할 사항🔹**  
간결하고 직관적인 표현과 일관성있고 명확한 구현,  
그리고 사이트의 특성을 이해하여 그에 맞는 기술을 사용하는 것이 중요하다.
