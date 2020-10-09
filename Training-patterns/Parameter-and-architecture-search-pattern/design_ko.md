# Parameter and architecture search pattern

## Usecase
- 모델의 파라미터와 아키텍처를 자동으로 탐색하고 싶을 경우.
- 수동으로 모델을 조정하기 어려울 경우.

## Architecture
Parameter and architecture search pattern은 하이퍼 파라미터와 아키텍처 탐색을 자동으로 하는 것을 목표로 합니다. 데이터 세트와 평가를 바탕으로 하이퍼 파라미터와 아키텍처를 자동으로 탐색할 수 있게 함으로써 모델 개발에서 수동 업무를 줄일 수 있습니다. 하이퍼파라미터는 학습 과정이 시작되기 전에 설정되는 값으로, 예를 들어 의사결정 나무(Decisiontree)의 깊이, 멀티레이어 퍼셉트론(Multilayer perceptron)에서 활성화 기능 등이 있습니다. 하이퍼 파라미터 탐색 방법으로는 그리드 서치, 랜덤 서치, 진화 알고리즘(Evolutionary algorithm), 그리고 베이지안 최적화(Bayesian optimization) 등이 있습니다. 아키텍처는 인셉션과 신경망에서 레스넷(Resnet)과 같은 모델의 전체적인 구조를 말합니다. 아키텍처 탐색에서는 강화 학습의 Neural architecture search와 Gradient descent 이용 방법이 있습니다. 위 방법들은 최적화된 머신러닝 모델을 찾기 위한 방법들입니다.<br>
 이 파이프라인은 탐색->학습->평가의 사이클로 실행됩니다. 모델 학습 구현 과정에서 이 패턴을 사용할 수 있습니다. 이 패턴에서는 탐색 메커니즘을 추가하고 동시에 모델을 최적화하며 학습시키는 것을 목표로 하고 있습니다. 이 경우, 학습용 파이프라인 외에 탐색에 대한 파라미터 구성을 해야 합니다. 먼저, 학습용 데이터셋을 검색한 후, 모델을 검색하고 평가하기 위한 파라미터를 사용하여 학습 작업이 실행됩니다. 일부 검색 메커니즘은 학습할 다음 하이퍼파라미터 또는 아키텍처를 선택합니다. 탐색→학습→평가의 사이클은 반복 횟수, 후보 파라미터의 개수, 시간 그리고 평가 목표치 등에 따라 사이클이 완료됩니다. 이를 통해 생성된 모델은 마지막에 최적인 모델로 모델 관리시스템에 기록합니다. <br>
이미 목적에 맞는 베스트 프렉티스가 확립되어 있거나, 전이 학습이나 재학습으로 좋은 모델을 만들 수 있다면 이 패턴은 적합하지 않습니다. 특정 문제에 대한 새로운 모델 탐색 혹은 최적화가 필요할 때 유용한 패턴입니다. 

## Diagram
![diagram](diagram.png)


## Pros
- 머신러닝 모델 자동 튜닝.
- 수동으로 확인 할 수 없는 모델 탐색.

## Cons
- 탐색할 파라미터 값.
- 계산을 위한 비용 발생.

## Needs consideration
- 파라미터 탐색 혹은 아키텍쳐 탐색.
- 파라미터 탐색과 아키텍쳐 탐색을 위한 알고리즘. 
- 알고리즘에 대한 파라미터 값. 
- 비용.