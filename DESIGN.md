# 오늘의 타로 (Taro) — 디자인 시스템 가이드 (DESIGN.md)
> **컨셉:** Scholar's Parchment & Mystic Ink (정갈한 양피지 위의 신비로운 먹물과 타로)

**Theme:** Warm Light (Parchment)  
**Target:** 모바일 퍼스트 웹 서비스 (Mobile Max-Width: 440px, 데스크톱 중앙 정렬 max-width: 900px)  
**기반 레퍼런스:** Perplexity AI 스타일 시스템 + Tailwind CSS v4 + shadcn/ui

---

## 1. 디자인 철학 및 비주얼 메타포

- **따뜻한 양피지와 정갈한 먹물 (Parchment & Ink)**:  
  눈부신 순백색(`#FFFFFF`) 대신, 손때 묻은 고서와 학자의 연구실을 연상시키는 **웜톤 오프화이트 양피지(`#FAF8F5`)**를 기본 캔버스로 사용합니다. 텍스트는 순흑색이 아닌 **깊은 웜블랙 잉크(`#27251E`)**로 표현하여 편안하고 정돈된 신뢰감을 줍니다.
- **절제된 딥 틸(Deep Teal) 시그널**:  
  과도한 보라색이나 현란한 그라데이션 대신, 학구적이면서도 신비로운 **딥 틸(`#016A71`)** 단 하나의 유채색만을 네비게이션, 활성 칩, 강조 배지에 사용하여 인터페이스의 차분함과 집중도를 유지합니다.
- **플랫한 종이 질감의 입체감 (Low Elevation)**:  
  과장된 그림자나 블러 대신, 1px의 **웜 미스트(Warm Mist, `#D1D1CD`)** 연필선 같은 테두리와 1단계 밝은 **소프트 페이퍼(`#FDFBFA`)** 면 분할로 층위를 구성합니다.
- **안심을 주는 프라이버시 인터페이스**:  
  "개인정보는 서버에 저장되지 않고 폰에서 즉시 폐기된다"는 원칙을 부드러운 자물쇠 아이콘과 절제된 캡션 배지로 녹여내어 사용자가 부담 없이 즉시 몰입할 수 있도록 돕습니다.

---

## 2. 디자인 토큰 (Tokens)

### 2.1 색상 (Color Palette)

| 토큰명 | CSS 변수 | HEX 값 | 역할 및 컴포넌트 적용 |
|:---|:---|:---|:---|
| **Parchment** | `--color-parchment` | `#FAF8F5` | 전체 페이지 캔버스 배경, 모바일 컨테이너 기본 배경 |
| **Soft Paper** | `--color-soft-paper` | `#FDFBFA` | 결과 카드(S-03), 정보 입력 박스 표면, 1단계 위 서피스 |
| **Warm Mist** | `--color-warm-mist` | `#D1D1CD` | 1px 헤어라인 구분선, 비활성 입력창/버튼 테두리 |
| **Ash** | `--color-ash` | `#92918B` | 보조 캡션, 힌트 텍스트, 날짜 플레이스홀더 |
| **Graphite** | `--color-graphite` | `#72706B` | 보조 텍스트, 비활성 칩 라벨, 오락용 안내 문구 |
| **Ink** | `--color-ink` | `#27251E` | 본문 타이포그래피, 주요 아이콘, 주 액션 버튼(Filled) 배경 |
| **Pure Black** | `--color-pure-black` | `#000000` | 타로 카드 명칭(로마자 표기 등) 극소수 고대비 강조 |
| **Deep Teal** | `--color-deep-teal` | `#016A71` | 선택된 주제 칩, 주요 상태 활성화, 별자리/강조 배지 |
| **Teal Glow** | `--color-teal-glow` | `rgba(1, 106, 113, 0.15)` | 카드 선택 포커스 링, 인터랙션 하이라이트 |

---

### 2.2 타이포그래피 (Typography)

한국어 환경에 최적화된 시스템 폰트 및 프리텐다드/Inter 조합을 적용하며, 굵기(Weight)는 **400(Regular)**과 **500(Medium)**, 제목 강조에만 **600(SemiBold)**을 사용하여 차분하고 단정한 서체 톤을 유지합니다.

| 역할 (Role) | Tailwind 클래스 | Size / Line-height | Weight | 용도 |
|:---|:---|:---|:---|:---|
| **Display** | `text-2xl` | 24px / 1.33 | 600 | S-01 메인 타이틀, 타로 카드 이름 ("XIX 태양") |
| **Title** | `text-lg` | 18px / 1.4 | 600 | S-02 섹션 헤더, S-03 결과 요약 ("지민님의 타로 · 커리어") |
| **Body-lg** | `text-base` | 16px / 1.5 | 400 | 맞춤 3줄 해석 본문, 주요 입력창(Input) |
| **Body** | `text-sm` | 14px / 1.43 | 400 | 주제 칩 라벨, 버튼 텍스트, 안내 텍스트 |
| **Caption** | `text-xs` | 12px / 1.4 | 400 | 개인정보 폐기 안내문, 생년월일 도움말 |
| **Micro** | `text-[11px]` | 11px / 1.3 | 500 | "저장 안 해요" 프라이버시 배지, 오락용 안내 라벨 |

---

### 2.3 간격 및 형태 (Spacing & Shapes)

- **기본 그리드 유닛**: 4px
- **레이아웃 최대 너비**: 
  - 모바일 뷰포트 컨테이너: `max-w-[440px]` (가운데 정렬)
  - 데스크톱 프레임: `max-w-[900px]`
- **간격 스케일**:
  - 요소 간 간격: `gap-2` (8px), `gap-3` (12px), `gap-4` (16px)
  - 섹션 간 여백: `py-6` (24px) ~ `py-8` (32px)
  - 카드 내부 여백: `p-4` (16px) ~ `p-5` (20px)
- **곡률 (Border Radius)**:
  - 타로 카드 및 결과 프레임: `rounded-2xl` (16px)
  - 입력 필드(Input), 주 버튼(Button): `rounded-xl` (12px)
  - 보조/고스트 버튼(Ghost Button): `rounded-lg` (8px)
  - 주제 선택 칩, 뱃지: `rounded-full` (9999px)
- **그림자 (Shadow)**:
  - 기본 평면 원칙: `shadow-none`
  - 결과 카드에만 미세한 단일 그림자 적용: `shadow-[0_1px_3px_rgba(0,0,0,0.06)]`

---

## 3. 화면별 컴포넌트 상세 명세

### 3.1 [S-01] 시작 화면
- **카드 뒷면 일러스트**: 양피지 질감 테두리에 미스틱 잉크 문양이 들어간 카드 실루엣 (`w-36 h-56`, `rounded-2xl`, 1px Warm Mist 보더).
- **메인 타이틀**: `오늘의 타로`, 부제 `내 정보를 넣고 카드 한 장으로 나만의 해석을 받아 봐요`.
- **시작 버튼 (Filled)**:
  - 배경: `--color-ink` (`#27251E`)
  - 텍스트: `--color-parchment` (`#FAF8F5`)
  - 크기: `w-full h-12 rounded-xl text-base font-medium`
- **안내 캡션**: `※ 오락용 타로 · 정보는 저장 안 해요` (`text-ash text-xs text-center`).

### 3.2 [S-02] 내 정보 및 주제 선택 화면
- **뒤로가기/헤더**: 간결한 텍스트 헤더 `나에 대해 알려 주세요`.
- **입력 폼 필드 (Input)**:
  - 이름: 최대 10자, 플레이스홀더 `지민 (닉네임 가능)`
  - 생년월일: `YYYY . MM . DD` 형식의 8자리 숫자 입력
  - 전공(선택): 플레이스홀더 `경영학과 (선택 입력)`
  - 스타일: `bg-soft-paper border border-warm-mist rounded-xl px-4 py-3 text-ink focus:border-deep-teal focus:ring-1 focus:ring-deep-teal`
- **주제 선택 칩 그리드 (Pill Chips)**:
  - 6개 항목: `💼 커리어`, `💰 재물`, `💕 연애`, `🌿 건강`, `📚 학업`, `✨ 종합`
  - 3열 2행 그리드 배치 (`grid-cols-3 gap-2`)
  - 기본 상태: `bg-transparent border border-warm-mist text-graphite rounded-full py-2 px-3 text-sm`
  - 선택(Active) 상태: `bg-deep-teal text-white border-deep-teal font-medium`
- **보안/프라이버시 박스**:
  - `bg-soft-paper/60 border border-warm-mist/60 rounded-xl p-3 text-xs text-graphite`
  - 자물쇠 아이콘(`🔒`)과 함께 `입력한 정보는 해석을 만드는 데만 쓰고 저장하지 않아요.` 명시.
- **카드 뽑기 버튼**:
  - 이름, 생년월일, 주제가 모두 충족되었을 때만 활성화 (`disabled:opacity-40 disabled:cursor-not-allowed`).

### 3.3 [S-03] 맞춤 해석 결과 카드 및 액션
- **결과 카드 컴포넌트 (1080×1350 이미지 저장 대상 영역)**:
  - 비율: 인스타그램 스토리 및 카드 저장 규격 (4:5 비율 최적화)
  - 표면: `bg-soft-paper border border-warm-mist rounded-2xl p-6 shadow-sm`
  - 카드 뒤집기 애니메이션: 3D flip 효과 (`perspective: 1000px`, `transform: rotateY(180deg)`, 지속시간 0.8초)
  - 헤더: `{이름}님의 타로 · {주제}` + `{별자리 뱃지}`
  - 카드 그래픽 및 이름: 정방향 메이저 아르카나 일러스트 + `XIX 태양 (The Sun)`
  - 3줄 해석 본문:
    ```
    1행 (카드 × 주제): 준비한 것을 드러낼 때예요.
    2행 (별자리 문장): 사자자리의 자신감이 무기가 돼요.
    3행 (전공 계열 문장): 경영학도다운 기획력이 빛나요.
    ```
  - 푸터: `※ 오락용 타로 해석입니다 · 오늘의 타로`
- **하단 액션 버튼 그룹**:
  - 1행: `[ 📥 이미지 저장 ]` (주 액션, Ink 버튼) + `[ 🔗 결과 공유 ]` (보조, Ghost/Border 버튼)
  - 2행: `[ 다시 뽑기 ]` (같은 정보로 주제 선택) + `[ 처음으로 ]` (정보 즉시 삭제 후 S-01 이동)

---

## 4. shadcn/ui 컴포넌트 커스터마이징 매핑

shadcn/ui 기본 컴포넌트를 Parchment 테마에 맞춰 매핑합니다:

### Button (`components/ui/button.tsx`)
- **default**: `bg-[#27251E] text-[#FAF8F5] hover:bg-[#1A1813] rounded-xl font-medium`
- **secondary**: `bg-[#016A71] text-white hover:bg-[#01585E] rounded-xl`
- **outline**: `border border-[#D1D1CD] bg-transparent text-[#27251E] hover:bg-[#FAF8F5] rounded-xl`
- **ghost**: `hover:bg-[#D1D1CD]/20 text-[#72706B] hover:text-[#27251E] rounded-lg`

### Input (`components/ui/input.tsx`)
- `bg-[#FDFBFA] border-[#D1D1CD] text-[#27251E] placeholder:text-[#92918B] rounded-xl focus-visible:ring-1 focus-visible:ring-[#016A71] focus-visible:border-[#016A71]`

### Badge (`components/ui/badge.tsx`)
- **default (Teal)**: `bg-[#016A71] text-white rounded-full text-[11px] font-medium px-2.5 py-0.5`
- **outline**: `border-[#D1D1CD] text-[#72706B] rounded-full text-[11px]`

### Card (`components/ui/card.tsx`)
- `bg-[#FDFBFA] border-[#D1D1CD] rounded-2xl shadow-[0_1px_3px_rgba(0,0,0,0.06)]`

---

## 5. Tailwind CSS v4 테마 설정 (`globals.css`)

```css
@import "tailwindcss";

@theme {
  /* Colors */
  --color-parchment: #faf8f5;
  --color-soft-paper: #fdfbfa;
  --color-warm-mist: #d1d1cd;
  --color-ash: #92918b;
  --color-graphite: #72706b;
  --color-ink: #27251e;
  --color-pure-black: #000000;
  --color-deep-teal: #016a71;
  --color-teal-glow: rgba(1, 106, 113, 0.15);

  /* Border Radii */
  --radius-button: 12px;
  --radius-card: 16px;
  --radius-chip: 9999px;

  /* Shadows */
  --shadow-card: 0 1px 3px rgba(0, 0, 0, 0.06);

  /* Animation */
  --animate-flip: flipCard 0.8s cubic-bezier(0.4, 0, 0.2, 1) forwards;
}

@keyframes flipCard {
  0% {
    transform: rotateY(0deg) scale(0.95);
  }
  50% {
    transform: rotateY(90deg) scale(1.05);
  }
  100% {
    transform: rotateY(0deg) scale(1);
  }
}
```

---

## 6. 디자인 Do's & Don'ts

### ✅ Do
- **배경은 항상 Parchment(`#FAF8F5`)**: 순백색(`#FFFFFF`) 대신 미색의 종이 질감 캔버스를 유지합니다.
- **유채색은 Deep Teal(`#016A71`) 단 하나만**: 시각적 주의가 분산되지 않도록 액센트 색상을 엄격히 통제합니다.
- **3줄 해석의 엄격한 글자 수 제어**: 결과 카드가 모바일 한 화면과 1080×1350 이미지에 완벽히 들어오도록 90자 이내를 준수합니다.
- **개인정보 폐기 강조**: 사용자가 안심할 수 있도록 자물쇠 아이콘과 폐기 문구를 시각적 노이즈 없이 정돈되게 배치합니다.

### ❌ Don't
- **보라색/네온 등 타로 클리셰 남발 금지**: 저렴한 운세 사이트처럼 보이지 않도록 과도한 그라데이션, 별빛 반짝임 효과를 배제합니다.
- **무거운 드롭 섀도우 지양**: 종이 위의 담백한 레이아웃을 해치는 짙은 그림자나 블러 효과를 쓰지 않습니다.
- **Bold(700+) 서체 남용 금지**: 제목 일부를 제외하고는 400~600 범위 내에서 크기와 색상 대비로 위계를 표현합니다.
- **단정적인 예언 어조 지양**: "돈을 벌게 됩니다" 대신 "지출 우선순위를 돌아볼 때예요"와 같은 따뜻하고 열린 관점의 문구를 유지합니다.
