# DESIGN.md — 건축 포트폴리오 (따뜻한 미니멀)

> 건축사무소 홈페이지 스타일에서 뽑은 디자인 지침서 예시입니다. 1주차 오프닝에서 본 페이지와 같은 분위기입니다.
> 쓰는 법: 이 파일을 내 랜딩페이지 폴더(`my-landing`)에 **DESIGN.md** 라는 이름 그대로 넣습니다. 히어로 렌더를 만드는 문장은 맨 아래 **부록 A**에 있습니다.
>
> **페이지를 만드는 AI에게**: 아래 규칙을 숫자까지 따른다. 내용(이름 · 작품 · 글 · 숫자 · 수상)은 폴더 안의 `소개.txt`, `docs` 폴더, `images` 폴더에서만 가져오고 **지어내지 않는다.** 자료에 없는 섹션은 만들지 않는다.

## 1. 분위기
- 종이처럼 따뜻한 흰 바탕, 넓은 여백, 사진이 주인공. 건축 잡지와 설계사무소 웹사이트의 차분한 편집.
- 장식은 선(1px)과 여백으로만. 큰 명조 제목 + 작은 영문 라벨 + 숫자는 고정폭 글꼴.
- 움직임은 느리고 부드럽게. 튀거나 통통 튀는 효과는 쓰지 않는다.

## 2. 색
```css
:root{
  --paper:#F7F5F0;   /* 바탕: 따뜻한 종이 */
  --paper-2:#F0ECE4; /* 번갈아 쓰는 바탕 (소재, 연구와 수상) */
  --ink:#1C1B19;     /* 글자, 연락 섹션 바탕 */
  --sub:#6B675F;     /* 보조 글자 */
  --accent:#B5562E;  /* 강조색: 번호, 강조 한 단어, 버튼에만 */
  --line:#DDD8CE;    /* 구분선 */
  --on-dark:#F2EFE8; --on-dark-sub:#ADA79C; /* 어두운 바탕 위 글자 */
}
```
- 강조색은 하나만 쓴다. 기본은 테라코타 벽돌색(#B5562E). 내 작품과 어울리게 바꾸고 싶으면 아래 중 하나로 바꾼다: 짙은 초록 #2F4A3A(조경 · 목조), 먹청 #2B3A4A(콘크리트 · 유리), 황동 #9A7B4F(실내 · 전시).

## 3. 글꼴 (Google Fonts)
```html
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,500;0,600;1,400;1,500&family=IBM+Plex+Mono:wght@400;500&family=Noto+Sans+KR:wght@400;500;600&family=Noto+Serif+KR:wght@500;600;700&display=swap" rel="stylesheet">
```
| 쓰임 | 글꼴 | 크기 · 굵기 |
|---|---|---|
| 첫 화면 이름 | Noto Serif KR 600 | clamp(60px, 7.4vw, 150px), 줄간격 1, 자간 -0.035em |
| 이름 옆 영문 | Cormorant Garamond 기울임 400 | clamp(26px, 2.25vw, 44px) |
| 섹션 제목 | Noto Serif KR 600 | clamp(40px, 4.4vw, 76px), 자간 -0.025em |
| 작품 제목 | Noto Serif KR 600 | clamp(34px, 2.9vw, 54px) + 아래에 영문 제목(Cormorant 기울임, 회색) |
| 소개 큰 문장 | Noto Serif KR 500 | clamp(28px, 3.05vw, 52px), 줄간격 1.52 |
| 본문 | Noto Sans KR 400 | clamp(16px, .35vw + 12px, 18px), 줄간격 1.7, `word-break: keep-all` |
| 작은 영문 라벨 | Noto Sans KR 500 | 16px, 대문자, 자간 0.2em, 회색 |
| 번호 · 연도 · 쪽수 | IBM Plex Mono 400 | 16px, 강조색 (예: 01 / 03, Fig. 01, M—01) |
| 큰 숫자 · 연도 | Cormorant Garamond 500 | 숫자 카운터 clamp(58px, 4.7vw, 90px), 연표 연도 28px |

글자 크기는 16px보다 작게 쓰지 않는다.

## 4. 배치
- 본문 폭 1200px, 작품 섹션만 1440px. 좌우 여백 5vw (휴대폰 20px).
- 12칸 그리드, 칸 사이 24px.
- 섹션 위아래 여백 clamp(96px, 14vh, 170px). 섹션 사이에는 1px 구분선.
- 섹션 머리 = 작은 라벨(`02  SELECTED WORKS`, 번호는 강조색 고정폭) → 큰 한글 제목(왼쪽 7칸) → 설명 한 줄(오른쪽 5칸, 회색, 제목 아래쪽에 맞춤).
- 섹션 번호는 실제로 만든 섹션만 01부터 차례로 매긴다.

## 5. 페이지 구성 (위에서부터 이 순서, "선택"은 자료가 있을 때만)

### 5-1. 메뉴
- 맨 위에 고정. 처음에는 투명하고 글자는 흰색. 조금 내리면 종이색 반투명 바탕(블러 14px) + 아래 1px 선 + 글자 검정으로 바뀐다.
- 왼쪽: 한글 이름(명조 600, 21px) + 영문 이름(대문자, 자간 0.2em). 오른쪽: 실제로 있는 섹션 이름만(예: 소개 · 작품 · 연락). 마우스를 올리면 밑줄이 왼쪽에서 그어진다.
- 휴대폰: 메뉴 대신 "메뉴" 버튼 → 화면 가득 종이색 목록(01 소개 … 큰 명조).

### 5-2. 첫 화면 (히어로)
- 화면 높이 100%, 대표 렌더 `images/hero.jpg` **한 장만** `object-fit: cover`로 가득. 42초 동안 1.0 → 1.1로 아주 천천히 확대. (`hero-day.jpg` · `hero-night.jpg`는 6-1에서 쓴다.) `hero.jpg`가 없으면 작품 사진 중 가로가 가장 긴 것을 쓰고 그 사실을 알려 준다.
- **글자 자리는 렌더의 어둡고 빈 쪽**에 둔다. 렌더를 보고 정하되, 부록 A의 렌더 종류별 기본 자리는 이렇다.
  - A 해 질 녘 외관 · D 해 질 녘 조감: 왼쪽 아래
  - B 이른 아침 물가: 위쪽 왼쪽(하늘)
  - C 빛이 드는 실내: 그림자가 진 쪽의 아래
- 글자 쪽은 진하게, 반대쪽은 살짝 어둡게 한다(글자 쪽 0→52% 구간 rgba(12,11,10,.74)→0, 반대쪽 0→21% 구간 .5→0). 필름 같은 아주 옅은 노이즈를 13% 정도 겹친다.
- 글자 묶음: 작은 라벨 `ARCHITECTURE PORTFOLIO · 연도` → 큰 이름 → 영문 이름(기울임) → 한 줄 소개(`소개.txt`). 폭은 화면의 44%까지.
- 대표작 명세 카드(선택, 글자 반대쪽 아래, 폭 25vw, 최대 360px): 첫 줄에 작품 이름(명조 22px) + 영문(기울임) + `01 / 작품 수`, 그 아래 1px 선으로 나눈 표: 유형 / 위치 / 연도. 자료에 없는 칸은 뺀다.
- 처음 열릴 때: 사진이 가운데에서 위아래로 열리듯 나타나고(1.7초), 라벨 → 이름 → 영문 → 소개가 한 줄씩 아래에서 올라온다(0.45초부터 0.15초 간격, 1.5초). 메뉴와 명세 카드는 그 뒤에 서서히.

### 5-3. 흐르는 키워드 띠 (선택)
- `소개.txt`에 관심 · 연구 키워드가 있을 때만. 히어로 바로 아래, 종이색 바탕, 아래 1px 선. 키워드를 한 줄로 64초에 한 바퀴 천천히 흘린다. 마우스를 올리면 멈춘다.
- 키워드 = 한글(명조 500, clamp(30px, 3.2vw, 56px)) + 영문(Cormorant 기울임, 회색). 키워드 사이에 강조색 점(9px 원).

### 5-4. 소개
- 왼쪽 3칸에 라벨 `01 ABOUT`과 프로필 사진(`images/profile.jpg`, 4:5, 없으면 라벨만), 오른쪽 9칸에 소개 큰 문장. 강조할 말 하나만 강조색.
- 그 아래 두 칸 나눔: 왼쪽은 소속 · 학력 · 관심 · 도구 표(위아래 1px 선), 오른쪽은 작품 · 수상 · 논문 개수(자료에 있는 것만, 두 자리 03). 숫자는 화면에 들어오면 슬롯처럼 아래에서 위로 굴러 올라가며 맞춰진다.

### 5-5. 작품
- `images/work01.jpg`, `work02.jpg` … 작품마다 큰 이미지(8칸, 3:2) + 글(4칸). 짝수 번째 작품은 좌우를 바꾼다. 작품 사이 여백 clamp(110px, 18vh, 220px).
- 한 작품에 사진이 두 장 이상이면 작은 둘째 이미지(폭 37%, 4:3)를 큰 이미지 오른쪽 아래에 종이색 10px 테두리로 겹쳐 놓는다.
- 글: `01 / 작품 수`(고정폭, 강조색) → 제목(명조) → 영문 제목 → 설명 → 유형 · 위치 · 구조 · 규모 · 연도 표(1px 선, 자료에 있는 칸만). 이름 · 설명 · 연도는 `docs` 폴더의 포트폴리오나 `소개.txt`에서 가져온다. **설명이 없으면 이름과 연도만 쓰고 설명을 지어내지 않는다.**
- 이미지는 스크롤할 때 글보다 조금 느리게 움직이고(시차), 마우스를 올리면 1.035배로 천천히 커진다. 이미지를 눌렀을 때의 동작은 6-2에서 붙인다.

### 5-6. 아끼는 소재 (선택)
- `소개.txt`에 재료 이야기가 있을 때만. 바탕 --paper-2. 카드를 한 줄로(태블릿 3개, 휴대폰 2개).
- 카드 = 3:4 재질 견본 + `M—01` + 이름(명조) + 영문(기울임) + 설명(회색).
- 재질 견본은 사진 대신 SVG로 실제 표면처럼 그린다(예: 콘크리트는 거푸집 판 이음 + 폼타이 구멍 + 얼룩, CLT는 나뭇결 + 단면의 켜, 벽돌은 줄눈과 장마다 다른 색, 유리는 하늘 반사 + 멀리언, 코르텐강은 녹의 얼룩과 흘러내린 자국). 마우스를 올리면 1.06배.

### 5-7. 영감을 준 건축 (선택)
- `images/inspiration/` 폴더에 사진이 있고 `소개.txt`에 사진마다 **출처(촬영자 · 이용 조건 · 링크)** 가 적혀 있을 때만. 출처를 모르는 사진은 쓰지 않는다.
- 3칸 그리드(태블릿 2, 휴대폰 1), 사진은 4:3로 잘라 채움. 사진 아래: `Fig. 01`(강조색) ↔ 연도(오른쪽) → 건물 이름(명조) → 건축가 · 장소(회색) → 한 줄 → 1px 선 위에 사진 출처 한 줄.

### 5-8. 연구와 수상 (선택)
- `docs` 폴더나 `소개.txt`에 있을 때만. 바탕 --paper-2. 두 칸: 논문 · 연구 / 수상. 칸 제목은 명조 + 오른쪽에 개수(고정폭), 아래 검은 1px 선.
- 목록은 연도(Cormorant 28px) + 제목(명조 500) + 구분(회색)의 연표, 줄마다 1px 선.

### 5-9. 연락
- 바탕 --ink(거의 검정), 글자 --on-dark. 라벨 `CONTACT` → 큰 제목(명조 600, clamp(44px, 6vw, 110px), 두 줄, `소개.txt`의 한 줄 소개에 어울리게) → 한 줄 → 큰 이메일 주소(Cormorant 500, clamp(30px, 3.5vw, 60px), 밑줄).
- 알약 모양 버튼 두 개(높이 54px): "메일 보내기 →"(강조색 채움), "주소 복사"(외곽선, 누르면 "복사했습니다"). 그 아래 `소개.txt`에 적힌 공개용 연락처만(예: Email · Instagram).

### 5-10. 바닥글
- 연락과 같은 어두운 바탕. 사진 출처가 있으면 `PHOTO CREDITS` 아래에 2단으로. 맨 아래 `© 연도 이름`.

## 6. 나중에 따로 주문할 때 붙이는 부품

- 처음 페이지를 만드는 주문에서 따로 말하지 않았으면 이 절은 **만들지 않는다.** 사용자가 "비교하는 화면으로 바꿔줘", "크게 보이게 해줘"처럼 주문하면 그때 붙인다.

### 6-1. 이미지 비교 슬라이더 (비포 · 애프터 슬라이더, 첫 화면)
- 같은 구도의 낮 렌더(`images/hero-day.jpg`)와 해 질 녘 렌더(`images/hero-night.jpg`, 없으면 `hero.jpg`)를 정확히 겹친다. 두 장 모두 같은 `object-fit`, 같은 `object-position`, 같은 확대 애니메이션을 써야 건물이 어긋나지 않는다.
- 왼쪽이 낮, 오른쪽이 해 질 녘. 경계는 흰 1px 세로 분할선, 선 위(화면 높이 44% 지점)에 지름 58px 둥근 손잡이(흰 1px 테두리, 반투명 어두운 바탕 + 블러, 안에 ‹ › 화살표).
- 손잡이 양옆에 `낮 Day` / `해 질 녘 Dusk`(영문은 Cormorant 기울임). 손잡이 아래에 알약 모양 "끌어서 비교해 보세요" 안내, 한 번 만지면 사라진다.
- 마우스는 사진 어디를 눌러 끌어도, 휴대폰은 손가락으로 가로로 끌 때만 움직인다(세로 스크롤은 그대로). 키보드 ←→ 로도 움직인다.
- 처음 열릴 때 선이 0%에서 84%까지 2.7초 동안 천천히 지나갔다가 50%로 돌아와 멈춘다(힌트 애니메이션). 손대면 그 연출은 바로 멈춘다.

### 6-2. 작품 크게 보기
- 작품 글 맨 끝(표 아래)에 "크게 보기 →" 밑줄 버튼을 더하고, 이미지에 마우스를 올리면 오른쪽 위에 둥근 확대 아이콘이 나타나게 한다.
- 작품 이미지나 "크게 보기"를 누르면 거의 검은 바탕(#100F0E)에 화면 가득. 위: `01 / 전체 장수`(고정폭) + 닫기 둥근 버튼. 양옆: 이전 / 다음 둥근 버튼. 아래: 작품 이름(명조) + 설명 한 줄 + "← → 넘기기 · Esc 닫기".
- 모든 작품 이미지를 차례로 넘긴다. ← → 키, Esc, 휴대폰 좌우 밀기 모두 된다. 열려 있는 동안 뒤쪽 페이지는 스크롤되지 않는다.

## 7. 움직임
- 기본 곡선 `cubic-bezier(.19,1,.22,1)`. 대부분 1.2~1.8초.
- 섹션 글은 화면에 들어오면 아래 34px에서 떠오르며 나타난다. 이미지는 위아래가 살짝 가려졌다가 열리듯 나타난다(clip-path 7% → 0).
- 같은 묶음 안에서는 0.06~0.08초씩 늦게 차례로.
- 운영체제에서 "동작 줄이기"를 켠 사람에게는 움직임을 모두 끄고 바로 보여 준다.

## 8. 휴대폰 (가로 760px 이하)
- 좌우 여백 20px. 그리드는 한 줄로 쌓는다. 가로로 넘치는 곳이 하나도 없어야 한다.
- 첫 화면 이름 clamp(54px, 17vw, 86px), 명세 카드는 숨긴다. 렌더를 보고 건물이 화면 가운데 오도록 `object-position`을 정한다.
- 작품의 둘째 이미지는 큰 이미지 아래로 내려 오른쪽에 겹친다(폭 58%).

## 9. 하지 말 것
- 그라데이션 배경(사진 위 어둡게 하기는 예외), 이모지, 네온색, 그림자 남발, 둥근 모서리 카드 남발.
- 3D 모델, 아이콘 꾸러미, 외부 프레임워크. 아이콘이 필요하면 SVG 선(1.4px)으로 직접 그린다.
- 자료에 없는 수상 · 숫자 · 문장 · 경력을 지어내기.
- 주민번호 · 전화번호 · 집 주소 같은 개인정보 넣기.

## 10. 파일
- `index.html` 한 파일에 CSS와 JavaScript를 모두 넣는다. 이미지는 `images/…` 상대 경로 그대로 쓴다.
- 자료 폴더의 글은 UTF-8 한글이다.
- 만든 뒤 확인은 코드를 읽어서 빠르게 끝낸다(이미지 경로가 실제 파일 이름과 맞는지, 가로로 넘칠 곳이 없는지). 브라우저를 띄워 화면을 찍어 보는 확인은 하지 않는다. 화면은 사용자가 직접 열어 본다.

---

## 부록 A. 히어로 렌더 만들기 — 네 가지 종류

> **페이지를 만드는 AI에게**: 이 부록은 사람이 이미지 AI(예: Gemini 앱)에 붙여 넣는 문장이다. 페이지를 만들 때 이 문장으로 이미지를 만들지 않는다.

### 쓰는 순서
1. 내 작품에 어울리는 종류를 하나 고릅니다(아래 A~D).
2. 내 모델 화면 캡처(스케치업 · 라이노 등)가 있으면 이미지 AI에 첨부하고, 문장 맨 앞에 **모델 첨부용 첫 줄**을 붙입니다. 모델이 없으면 첫 줄 없이 씁니다.
3. [대괄호] 안을 내 설계에 맞게 바꿉니다. 한국어로 써도 됩니다.
4. 마음에 드는 결과를 `images/hero.jpg`로 저장합니다(가로 2400px 이상).
5. 이미지 비교 슬라이더(6-1)를 쓰려면, 4번 사진을 첨부하고 **낮 버전 문장**으로 같은 구도의 낮 사진을 만들어 `hero-day.jpg`로, 원래 사진은 `hero-night.jpg`로 저장합니다. 낮 사진을 따로 새로 만들면 창 위치가 달라져 비교할 때 건물이 어긋납니다.

AI 렌더는 **내 설계**를 사진처럼 보여 주는 데 씁니다. 내가 설계하지 않은 건물을 내 작품처럼 올리지 않습니다. 실제 모형 사진이 좋으면 그대로 히어로로 써도 됩니다.

**모델 첨부용 첫 줄**
```
Turn the attached model view into a photorealistic photograph. Keep the building's exact shape, openings, floor heights and proportions; do not add or remove anything.
```

### A. 해 질 녘 외관 — 주거 · 소규모 건물, 창이 많은 입면 (글자: 왼쪽 아래)
```
Photorealistic architectural photograph of [a four-storey timber apartment building with deep balconies] on [a quiet hillside alley corner in a Korean residential neighborhood]. Pedestrian eye level 1.6 m, 24mm tilt-shift lens, two-point perspective with straight verticals. Blue hour, about 20 minutes after sunset: deep cobalt sky with a faint warm glow at the horizon, warm 2700K light inside so each floor glows as a horizontal layer. Facade: [exposed timber slab edges, vertical battens, floor-to-ceiling glass, a planted roof terrace]. Context: older brick houses, a mature tree, a distant mountain ridge, slightly wet pavement with soft reflections, two pedestrians in motion blur. Building on the right two-thirds, a darker quiet left third for text. Calm, poetic mood of high-end Nordic archviz studios, restrained colors, subtle film grain. No text, no logos, no watermark. 16:9.
```

### B. 이른 아침 물가 · 수평 구도 — 도서관 · 공공건축 · 조경, 길고 낮은 건물 (글자: 위쪽 하늘)
```
Photorealistic architectural photograph of [a long, low public library with a deep cantilevered timber roof and a fully glazed reading hall] on the bank of [a calm river in a Korean city]. Shot from the opposite bank at water level, 35mm lens, straight verticals, calm horizontal composition with the building on the lower third. Early morning just after sunrise: thin mist over the water, soft pastel sky, warm low light catching the underside of the roof, the lit interior mirrored as a long still reflection. Reeds and a few willow trees in the foreground, a lone cyclist in slight motion blur, distant towers barely visible through the haze. Generous empty sky in the upper half for text. Serene, contemplative mood, desaturated natural palette, gentle film grain. No text, no logos, no watermark. 16:9.
```

### C. 빛이 드는 실내 — 예배당 · 전시장 · 실내가 중심인 작품 (글자: 그림자 쪽 아래)
```
Photorealistic interior architectural photograph of [a small chapel with board-formed concrete walls]. Eye level 1.5 m, 24mm lens, one-point perspective with straight verticals. A single shaft of late-afternoon sunlight falls through [a narrow skylight slot], drawing a sharp line of light across [the concrete wall and a polished stone floor], faint dust visible in the beam. [Simple timber benches], no people. The [left] half of the frame stays in deep, quiet shadow for text. Silent, contemplative mood, muted mineral palette, high dynamic range without halos, subtle film grain. No text, no logos, no watermark. 16:9.
```

### D. 해 질 녘 조감 — 단지 · 캠퍼스 · 도시재생처럼 넓은 계획 (글자: 왼쪽 아래)
```
Photorealistic aerial architectural photograph of [a low-rise housing cluster with shared courtyards and green roofs] in [a dense hillside neighborhood by the sea in Changwon]. Drone view from about 60 m at a 35-degree downward angle, 35mm lens. Golden hour: low warm sunlight raking across the roofs, long soft shadows, [timber pergolas and stepped gardens], surrounding older rooftops and narrow streets, the sea faintly visible in the haze. The new buildings sit in the right half; the lower-left quarter is calmer and darker for text. Natural colors, crisp detail, gentle atmospheric haze, editorial archviz style. No text, no logos, no watermark. 16:9.
```

### 같은 구도 낮 버전 (이미지 비교 슬라이더용, A · B · D에 사용)
```
Keep the exact same camera, composition, building geometry, windows, trees and surroundings. Change only the lighting and atmosphere to a bright late morning: soft daylight, clear blue sky with a few soft clouds, interior lights off, no people. Do not move or alter any object. 16:9.
```

### 결과가 이상할 때 덧붙이는 한 줄
```
Avoid cartoon or toy-like 3D look, plastic materials, oversaturated colors, bent verticals, warped railings, duplicated windows, text and watermark. Keep the number of windows and the proportions exactly as they are.
```
