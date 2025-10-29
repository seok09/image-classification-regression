# image-classification-regression
# 이미지 분류(Image Classification) vs 회귀(Regression)

## 1. 정의

### 이미지 분류 (Image Classification)
- 이미지가 **어떤 카테고리**에 속하는지 예측하는 문제
- 예시: 고양이 사진인지, 강아지 사진인지 맞추기
- 결과값: 범주(label) → 보통 **정수나 문자열** 형태
- 유형: **범주형 데이터(categorical)** 문제

### 회귀 (Regression)
- 이미지에 대해 **연속적인 값**을 예측하는 문제
- 예시: 사진 속 사람의 나이, 집값, 온도
- 결과값: **숫자(float)** → 연속적인 값
- 유형: **연속형 데이터(continuous)** 문제

---

## 2. 입력 데이터(Input)
- 둘 다 **이미지**를 입력으로 사용 가능
- 이미지 → 픽셀값 → 모델 입력

예시:

| 픽셀값 | 의미 |
|--------|------|
| [0, 255, 128, ...] | 이미지 밝기 및 색 정보 |

---

## 3. 출력 데이터(Output)

### 이미지 분류
- 출력: 클래스 확률
- 예시: 
  - `[0.8, 0.1, 0.1]` → 첫 번째 클래스(고양이) 확률 80%
  - 예측값: **가장 높은 확률 클래스 선택**

### 회귀
- 출력: 연속적인 숫자
- 예시:
  - `25.3` → 사람의 나이
  - `350000.0` → 집값

---

## 4. 사용되는 손실 함수(Loss Function)

| 문제 유형 | 손실 함수 예시 |
|-----------|----------------|
| 분류 | Cross-Entropy Loss, Focal Loss |
| 회귀 | Mean Squared Error (MSE), Mean Absolute Error (MAE) |

---

## 5. 모델 구조 차이

- 분류: 마지막 레이어 **Softmax** → 클래스 확률 계산
- 회귀: 마지막 레이어 **Linear/None** → 연속 값 출력

```text
이미지 -> CNN/ResNet -> Fully Connected -> Softmax -> 클래스 확률  # 분류
이미지 -> CNN/ResNet -> Fully Connected -> 숫자 출력                # 회귀
