# myCafe

> 내 주변 카페를 조회하고 후기를 작성합니다.



## 주요기능

- 현재 내 주변 카페, 후기를 작성한 카페, 후기를 작성하지 않은 카페를 조회합니다.
- 전국으로 원하는 카페를 검색합니다.
- 카페 후기를 작성, 수정합니다.
- 출발지, 도착지를 설정하여 길찾기를 할 수 있습니다.
- 베스트 리뷰어들을 조회하고, 그들이 쓴 카페 후기를 보며, 팔로우 합니다.



## 시작 가이드

### 요구사항

- Node.js 18.x 이상
- SQLite

### 실행

<pre><code>$ npm install
$ npm run dev
</code></pre>



<!-- ## 페이지 구성 -->

## 프로젝트 동기 및 목표

이전에 경험해보지 못한 지도를 이용한 서비스를 직접 만들어보며 싱글 페이지 안에서 복잡한 Context, State를 심화있게 학습 합니다. <br />
또한 Remix.js 프레임워크를 최대 활용해 서버까지 빠르게 구축해봅니다.



## 구현 내용

Kakao Map API를 활용해서 지도를 보고, 현재 사용자 위치 기반으로 카페를 조회할 수 있습니다. <br />
프로그램 주요 동작 방식은 다음과 같습니다. 카카오에서 제공하는 사용자 주변 45개의 카페 데이터를 기반으로 후기 작성 여부도 필터링해서 조회할 수 있습니다. 또한 현재 위치를 제외하고 사용자가 보고 있는 지도 중심을 기반으로 원하는 카페를 검색할 수 있습니다. 사용자는 방문한 카페 또는 후기를 작성한 카페에 후기를 작성하고, 수정할 수 있습니다. 가고 싶은 카페가 있다면 출발/도착지를 선택하여 자동차를 이용한 길찾기를 조회할 수 있습니다. <br />
사용자들이 작성한 후기를 통계내어 베스트 리뷰어 TOP 10을 선정해서 조회할 수 있습니다. 사용자는 원하는 리뷰어를 팔로우할 수 있으며, 리뷰어가 작성한 후기를 조회할 수 있습니다. 또한 사용자가 팔로잉한 리뷰어들만 조회할 수도 있습니다.



## 프로젝트를 진행하며 느낀점

실무에서 처음으로 Remix.js를 접했으나, Remix.js의 강점을 전혀 활용해보지 못한 느낌이 컸었습니다. <br />
그래서 이번 프로젝트에 Remix.js를 선택했고, Remix.js + Prisma + SQLite 조합을 선택한 이유는 생산성 측면에서 매우 빠른 개발이 가능하다고 판단했었는데, 확실히 SQL 문법에 조금 덜 익숙하더라도 빠르게 적응하여 개발 할 수 있었습니다. <br />
더불어 Remix.js가 V2로 업그레이드 되면서 점(.)을 이용한 파일 네이밍 시스템을 처음 알게되었는데, 이 규칙을 적극 활용하여 불필요한 Layout 컴포넌트를 줄일 수 있었습니다. <br />




## 아쉬운 점 및 개선 사항

1. 리뷰, 유저 데이터 외에는 모두 Kakao Map 데이터에 의존 되어있습니다. 카카오에서 제공하는 데이터는 한정적이고, 제가 보여주고 싶은 UI가 있다보니 코드의 복잡성이 높아졌습니다. 예를 들면 받아온 카페 데이터에 유저가 쓴 리뷰를 맵핑 해야할때, 45개 데이터를 한번에 보여주기위해 강제 반복문을 실행해야하는 형태 등등이 있었습니다. 이 부분에 대해선 리팩토링을 지속적으로 해주고 있으며, 추후에는 크롤링을 통한 자체 데이터를 수집하려는 목표를 가지고 있습니다.
2. 길찾기 제공 기능이 자동차밖에 없는 점이 아쉽습니다. 현재 자동차 길찾기는 Kakao 모빌리티 API를 이용하고 있습니다. 현재 도보 이동 기능을 어떻게 제공할 수 있을지 알아보고 있는 중입니다.