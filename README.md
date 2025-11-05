#McCabe-Thiele-Method

JavaScript로 구현한 McCabe-Thiele 증류탑 계산기입니다. 

머피 단 효율(Murphree Efficiency)을 적용하여 실제 단수를 계산하는 기능에 중점을 두었습니다.

<img width="2174" height="1439" alt="image" src="https://github.com/user-attachments/assets/24295ae3-6ac9-4594-95e7-f2540fdbb1bb" />

#주요 기능

이성분계(메탄올-물) 증류탑의 McCabe-Thiele 작도 시각화q-line, 정류부 조작선(ESOL), 탈거부 조작선(SSOL), 핀치 포인트(Pinch Point)를 이용한 최소 환류비($R_{min}$) 자동 계산

머피 효율($n_m$)을 적용한 유효 평형 곡선(Effective Equilibrium Curve) 생성유효 평형 곡선을 기준으로 스테핑하여 실제 단수($N_{actual}$) 계산

#핵심 작동 원리

이 계산기는 사용자가 입력한 값(xd, xb, zf, q, R/Rmin)을 바탕으로 최소 환류비($R_{min}$)와 실제 조작선(ESOL, SSOL)을 계산합니다.

머피 효율의 적용가장 큰 특징은 이상 단수를 계산한 뒤 효율로 나누는 방식이 아니라, 머피 효율의 정의를 작도에 직접 적용하는 것입니다.


$y_{effective} = y_{op} + n_m \times (y_{ideal} - y_{op})$


위의 식을 사용하여, 이상 평형 곡선(y_ideal)과 조작선(y_op) 사이의 거리를 머피 효율($n_m$)만큼 축소시킨 **새로운 '유효 평형 곡선'**을 생성합니다.

이후, 단수 계산(Stepping)은 본래의 이상 평형 곡선이 아닌, 이 유효 평형 곡선을 기준으로 수행하여 실제와 더 가까운 단수를 도출합니다.


#사용한 기술

HTML: 계산기 인터페이스

JavaScript (ES6 Modules):모든 핵심 계산 로직 (이진 탐색, 선형 보간, 조작선 계산), DOM 조작 및 이벤트 처리
