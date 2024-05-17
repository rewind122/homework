# apple 제품 카드
![애플 제품 카드 동작 이미지](./homework-apple.gif)

### HTML 마크업
- 카드 컴포넌트
  ```html
  <div class="card">
    <h1 class="product-name">iPad Pro</h1>
    <h2 class="product-info">
      놀라우리만치 얇다.<br />
      엄청나게 강력하다.
    </h2>
    <span class="release-date">출시일 추후 공개</span>
    <div class="info-link-group">
      <a href="/" class="more-info">더 알아보기</a>
      <a href="/" class="price-info">가격 보기</a>
    </div>
  </div>
  ```
  - 각 카드 컴포넌트는 **card**라는 클래스를 가진 `div` 요소로 내용을 감쌌습니다. 제목과 부제목은 각각 `h1`과 `h2` 요소로, 출시일 텍스트는 `span` 요소로, 링크 버튼은 `a` 요소로 마크업하고 각각의 내용에 맞는 클래스를 넣어줬습니다.
  - 컴포넌트 내 링크 버튼의 배치를 수월하게 하기 위해 두 링크 버튼을 `div` 요소로 묶어줬습니다.

- 작성한 컴포넌트 마크업을 카드 개수에 맞게 복사해 붙여넣었습니다. 그리고 전체 카드의 배치를 위해 전체를 감싸는 **card-container**라는 클래스를 가진 `div` 요소를 만들었습니다. 

### CSS 스타일링
- 카드 컴포넌트
  ```css
  .card {
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 50% 50%;
    width: 100%;
    height: var(--size);
    padding-top: var(--large-spacing);
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
    row-gap: var(--small-spacing);

    .product-name {
      font-size: var(--large-text);
      font-weight: 700;
    }

    .product-info {
      font-size: var(--base-text);
      text-align: center;
      line-height: var(--line-normal);
    }
  }
  ```
  - 카드 컴포넌트의 공통 속성을 작성해줍니다.
  - 반응형으로 움직이는 배경을 위한 속성을 `.card` 안에 작성합니다. 사이즈는 **cover**로, 너비는 **100%**로 넣어주고, 예시와 동일한 움직임을 위해 배경의 포지션도 중앙으로 조절해줍니다.
  - 카드 내부 요소의 배치를 위해 `.card` 요소를 플렉스 컨테이너로 만들고 필요한 속성을 함께 적어줍니다.
  - 제시된 값에 맞춰 제목과 부제목의 css도 작성해줍니다.
  ```css
  .info-link-group {
    display: flex;
    flex-flow: row nowrap;
    column-gap: var(--base-spacing);

    a {
      padding: var(--x-small-spacing) var(--small-spacing);
      border-radius: 100px;
      font-size: var(--xx-small-text);
      flex: 0 1 auto;
    }
  }
  ```
  - 링크 버튼 묶음 또한 플렉스 컨테이너로 만들어 두 버튼을 가로로 배치해줍니다. 이후 제시된 값에 맞춰 css를 작성합니다.
  ```css
  .card {

    .release-date {
      font-size: var(--small-text);
      color: var(--gray);
    }

    &.prv-product {

      .release-date {
        display: none;
      }
    }
  }
  ```
  - '출시일 추후 공개'라는 글자가 노출이 되는 카드는 상단 두 개뿐이므로, 나머지 카드들에는 보이지 않게 만들기 위해 클래스를 추가해 스타일링을 작성했습니다. **prv-product**라는 클래스를 가진 카드는 텍스트가 노출되지 않도록 `display: none;` 값을 넣어주고, 해당되는 요소의 클래스로 추가해줬습니다.
- 테마별 색상
  ```css
  .dark {
    color: var(--white);

    .more-info{
      background-color: var(--blue-100);
      border: 1px solid var(--blue-100);
    }

    .price-info {
      border: 1px solid var(--blue-100);
      color: var(--blue-100);
    }
  }

  .light {
    color: var(--black);

    .more-info{
      background-color: var(--black);
      border: 1px solid var(--black);
      color: var(--white);
    }

    .price-info {
      border: 1px solid var(--black);
    }
  }
  ```
  - 배경 이미지의 주 색상에 따라 글자색이 달라지는 것은 각각 다른 클래스를 지정해 스타일링을 해주는 게 더 편할 것 같아서 별도로 작성했습니다. 작성 후 각 카드 컴포넌트마다 해당되는 테마의 클래스를 넣어줬습니다.
- 제품별 배경 이미지 셋
  ```css
  .ipad-pro {
    background-image: image-set(
      url(./../products/ipad_pro.jpeg) 1x,
      url(./../products/ipad_pro_2x.jpeg) 2x);
  }
  .ipad-air {
    background-image: image-set(
      url(./../products/ipad_air.jpeg) 1x,
      url(./../products/ipad_air_2x.jpeg) 2x);
  }
  .iphone-15-pro {
    background-image: image-set(
      url(./../products/iphone15_pro.jpeg) 1x,
      url(./../products/iphone15_pro_2x.jpeg) 2x);
  }
  .iphone-15 {
    background-image: image-set(
      url(./../products/iphone15.jpeg) 1x,
      url(./../products/iphone15_2x.jpeg) 2x);
  }
  .watch {
    background-image: image-set(
      url(./../products/apple_watch.jpeg) 1x,
      url(./../products/apple_watch_2x.jpeg) 2x);
  }
  .macbook-air {
    background-image: image-set(
      url(./../products/macbook_air.jpeg) 1x,
      url(./../products/macbook_air_2x.jpeg) 2x);
  }
  .airpods-pro {
    background-image: image-set(
      url(./../products/airpods_pro.jpeg) 1x,
      url(./../products/airpods_pro_2x.jpeg) 2x);
  }
  ```
  - 수정 편의성을 위해 각 제품 카드별 배경이미지는 제품 이름 클래스를 만들어 작성해주고, 해당되는 제품 카드에 맞게 클래스를 넣어줬습니다.
- 모바일 카드 레이아웃
  ```css
  .card-container {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: var(--base-spacing);

    .card {
      grid-column: span 2;
    }
  }
  ```
  - 데스크톱 환경에서의 배치도 고려해 `.card-container`를 2열 그리드 컨테이너로 만들고, 모든 카드들이 2열을 다 차지하도록 해줍니다.
- 데스크톱 카드 레이아웃 
  ```css
  @media (min-width: 1024px) {
    .card-container {

      .card:nth-child(n+4) {
        grid-column: span 1;
      }
    }

    .card {
      padding-top: var(--extra-large-spacing);
    
      .product-name {
        font-size: var(--extra-large-text);
      }
    
      .product-info {
        font-size: var(--medium-text);
      }
    
      .info-link-group a{
        font-size: var(--x-small-text);
      }
    }

    .ipad-pro {
      background-image: image-set(
        url(./../products/ipad_pro_wide.jpeg) 1x,
        url(./../products/ipad_pro_wide_2x.jpeg) 2x
      );
    }
    .ipad-air {
      background-image: image-set(
        url(./../products/ipad_air_wide.jpeg) 1x,
        url(./../products/ipad_air_wide_2x.jpeg) 2x
      );
    }
    .iphone-15-pro {
      background-image: image-set(
        url(./../products/iphone15_pro_wide.jpeg) 1x,
        url(./../products/iphone15_pro_wide_2x.jpeg) 2x
      );
    }
  }
  ```
  - 미디어 쿼리에 데스크톱 환경에서의 변경 사항을 넣어줍니다. 네번째 카드부터 일곱번째 카드까지는 2열 레이아웃으로 들어가기 때문에 **nth-child**를 이용해 해당 카드들만 선택해 배치를 변경해줍니다.
  - 그 외에 폰트 크기 및 여백, 배경 이미지 등 변경사항도 함께 작성해줍니다.

### 과제를 하며 느낀 점
- 수업시간에 배운 css 코드를 미리 작성해두고 html에 클래스로 조립하는 방식을 응용해보려고 노력했다. 생각보다 재미있기도 했는데 어떻게 써야 더 효율적일지는 계속 고민해봐야 하는 것 같다.
- '출시일 추후 공개' 텍스트는 아예 마크업 단계에서 지우는 것도 고려해봤는데 일단은 css로 노출 여부를 조절하는 방향으로 작성해봤다. 없는 걸 추후 보이게 하는 것보다는 있는 걸 안 보이게 만드는 게 쉬울 것 같아서 이렇게 작성했는데 뭔가 계속 아쉽다는 느낌이 든다...
- 요소의 가로 너비 설정에 따라 자꾸 가로 스크롤이 생기기도 해서 힘들었다. 어떻게 없애는 데는 성공했지만 완벽하게 이해하고 고쳐낸 게 아니라서 공부가 더 많이 필요하다고 느꼈다.
- 그리드는 정말 신기하지만 어렵다... 플렉스보다 훨씬 복잡한 느낌이라 좀더 여러가지로 사용해봐야 익숙해질 것 같다.