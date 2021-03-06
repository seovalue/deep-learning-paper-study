# CNN Keyword

먼저 논문을 읽기에 앞서, 첫번째 논문이므로 CNN 논문에 나오는 용어들에 대해 알아보자.  

* FC Layer(Fully Connected Layer): 이전 레이어의 모든 노드가 다음 레이어의 모든 노드에 연결된 레이어.

사진 데이터로 Fully Connected 신경망을 학습 시킬 때에는 3차원 사진 데이터를 1차원으로 평면화시켜야한다. 사진데이터를 평면화 시키는 과정에서 손실되는 공간 정보 유실로 인해 인공 신경망의 특징 추출 및 학습이 비효율적이고 정확도를 높이는 데에 한계가 있다.
즉, 이러한 한계를 극복하기 위해 공간 정보를 유지한 상태로 학습이 가능한 모델이 **CNN(Convolutional Neural Network)**이다.


## CNN의 장점
- 각 레이어의 입출력 데이터의 형상 유지
- 이미지의 공간 정보 유지
- 인접 이미지와의 특징을 효과적으로 인식
- 복수의 필터로 학습
- 학습 파라미터가 적음

## CNN의 주요 용어
### Convolution (합성곱)
합성곱 연산은 입력 데이터에 필터를 거쳐 출력을 만들어낸다. (합성곱 계층의 출력 이미지)

### Channel (채널)
컬러 이미지는 3차원 데이터로 3개의 채널로 구성된다. (Red, Green, Blue)
흑백 명암만을 표현하는 이미지는 2차원 데이터로 1개 채널로 구성된다.  
[참고](https://en.wikipedia.org/wiki/Channel_(digital_image))

### Filter (필터)
필터는 이미지의 특징을 찾아내기 위한 공용 파라미터이다. Filter를 Kernel 이라고 하기도 한다.
CNN에서는 Filter와 Kernel은 같은 말로 쓰인다. 
CNN에서 학습의 대상은 필터 파라미터이다. 입력 데이터를 지정된 간격으로 순회하여 채널별로 합성곱을 하고, 모든 채널의 합성곱의 합을 Feature Map으로 만든다.
Convolution Layer의 최종 출력 결과가 Activation Map

### Padding (패딩)
Convolution 레이어의 출력 데이터가 줄어드는 것을 방지하는 방법이다. 입력 데이터의 외각에 지정된 픽셀만큼 특정 값으로 채워 넣는 것을 의미한다.
주로 0으로 채워넣는다. (외각을 "0"으로 둘러싸는 특징으로부터 인공 신경망이 이미지의 외각을 인식하는 학습 효과도 있음.)

### Pooling 레이어
Convolution Layer의 출력 데이터를 입력으로 받아서 출력 데이터의 크기를 줄이거나 특정 데이터를 강조하는 용도로 사용된다.  
ex. Max Pooling, Average Pooling, Min Pooling 등

### Sigmoid
binary classification에 적절한 함수이다. 일정 값을 기준으로 0인지 1인지 구분함으로써 분류하는 방식.
딥러닝에서는 특정 임계치를 넘을 때만 활성화되기 때문에 activation function 중의 하나로 구분되는 함수
0 < n < 1 사이의 값만 다루므로 결국 chain rule을 이용해 계속 값을 곱해나간다고 했을 때, 결과 값이 0에 수렴할 수 밖에 없다는 한계를 가지고 있으므로, 나중에는 1보다 작아지지 않게 하기 위한 대안으로 ReLU라는 함수를 적용하게 된다.

### ReLU
내부 hidden layer를 활성화 시키는 함수로 sigmoid를 사용하지 않고, ReLU라는 활성화 함수를 사용하게 되는데, 이 함수는 0보다 작은 값이 나온 경우 0을 반환하고, 0보다 큰 값이 나온 경우 그 값을
그대로 반환하는 함수다. 0보다 큰 값일 경우 1을 반환하는 sigmoid와 다르다. 따라서 내부 hidden layer에는 ReLU를 적용하고, 마지막 output layer에서만 sigmoid 함수를 적용하면 이전에 비해 
정확도가 훨씬 올라가게 된다.
https://miro.medium.com/max/833/1*nrxtwp6rzqdFhgYh0x-eVw.png
