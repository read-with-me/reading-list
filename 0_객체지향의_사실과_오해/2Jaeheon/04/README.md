# 객체지향 설계의 품질

객체의 세계에서는 협력이라는 문맥이 객체의 행동 방식을 결정한다. 중요한 것은 개별 객체가 아닌 객체들 사이에 이루어지는 협력이다. 객체지향 설계의 품질을 결정짓는 것은 여러 객체들이 모여 이뤄내는 협력의 품질이다. 훌륭한 객체지향 설계자는 객체 간의 요청과 응답에서 창발 하는 협력에 초점을 맞춰서 애플리케이션을 설계한다. 객체의 모양을 빚는 것은 객체가 참여하는 협력이다. 어떤 협력에 참여하는지가 객체의 필요한 행동을 결정하고, 필요한 행동이 객체의 상태를 결정한다.

# 협력

## 요청과 응답으로 협력하는 사람들

협력은 한 사람이 다른 사람에게 도움을 요청할 때 시작이 된다. 스스로 해결이 불가능할 때 다른 사람에게 요청하며, 요청을 받은 사람은 필요한 지식을 알거나 또 다른 사람에게 요청한다. 처리가 가능한 요청을 받은 사람은 일을 처리한 후 서비스 혹은 지식을 제공하면서 응답한다.

결과적으로 협력은 다수의 요청과 응답으로 구성되며 전체적으로 협력은 다수의 연쇄적인 요청과 응답의 흐름으로 구성된다.

### 범인은 누굴까?

엘리스는 재판장에 들어갔는데, 판사는 왕이었으며, 왕은 첫 번째 목격자를 부르라고 토끼에게 명령하고 토끼는 목격자를 불렀다. 첫 번째 목격자는 모자장수였다. 왕이 목격자인 모자장수에게 증언하라 말하자 모자장수는 재판과 상관없는 이야기만 내뱉었다. 왕은 이제 증언 보고 내려가라고 하였다.

위 이야기는 파이를 훔친 하트 잭에 관한 공판이 열리고 있는 법정을 묘사한 것이다. 이 공판의 목적은 하트 잭에게 죄가 잇는지 판단하고 죄가 있다면 어떤 형량을 부과할지 결정하는 것이다.

## 재판 속 협력

- 누군가가 왕에게 재판을 요청함으로써 재판이 시작된다.
- 왕이 하얀 토끼에게 증인을 부를 것을 요청한다.
- 왕의 요청을 받은 토끼는 모자 장수에게 증인석으로 입장할 것을 요청한다.
- 모자 장수는 증인석에 입장함으로써 토끼의 요청에 응답한다.
- 모자 장수의 입장은 왕이 토끼에게 요청했던 증인 호출에 대한 응답이기도 하다.
- 이제 왕은 모자 장수에게 증언할 것을 요청한다.
- 모자 장수는 자신이 알고 있는 내용을 증언함으로써 왕의 요청에 응답한다.

어떤 등장인물들이 특정한 요청을 받아들일 수 있는 이유는 그 요청에 대해 적절한 방식으로 응답하는 데 필요한 지식과 행동 방식을 가지고 있기 때문이다. 그리고 요청과 응답은 협력에 참여하는 객체가 수행할 책임을 정의한다.

# 책임

객체지향에서는 적절한 행동을 할 의무가 있는 경우 해당 객체가 책임을 가진다고 말한다. 객체지향 설계에서 가장 중요한 능력은 책임을 능숙하게 객체에게 할당하는 것이다. 책임은 객체에 의해 정의되는 응집도 있는 행위의 집합으로, 객체가 알아야 하는 정보와 객체가 수행할 수 있는 행위에 대해 개략적으로 서술한 문장이다. 즉, Doing과 Knowing으로 분류된다.

- 아는 것 (Knowing)
    - 정보에 관해서 알거나 관련된 객체 또는 자신이 유도하거나 계산할 수 있는 것에 관해 아는 것
- 하는 것 (Doing)
    - 객체를 생성하거나 계산하는 등 스스로 하거나 다른 객체의 행동을 시작시키고, 다른 객체의 활동을 제어 및 조절하는 것.

책임은 객체지향 설계의 품질을 결정하는 가장 중요한 요소이다. 책임은 일반적으로 외부에서 접근 가능한 공용 서비스의 관점에서 이야기한다. 즉, 책임은 객체의 외부에 제공해 줄 수 있는 정보와 외부에 제공해 줄 수 있는 서비스의 목록이다. 따라서 책임은 객체의 공용 인터페이스를 구현한다.

### 책임과 메시지

메시지는 협력을 위해서 한 객체가 다른 객체로 접근할 수 있는 유일한 방법이다. 책임이 협력이라는 문맥 속에서 요청을 수신하는 한쪽의 객체 관점에서 무엇을 할 수 있는지를 나열하는 것이라면 메시지는 협력에 참여하는 두 객체 사이의 관계를 강조한 것이다.

하지만 메시지의 수준과 책임은 같지 않다. 책임은 객체가 협력에 참여하기 위해 수행해야 하는 행위를 상위 수준에서 개략적으로 서술한 것이다. 책임을 결정한 후 실제로 협력을 정제하면서 이를 메시지로 변환할 때는 하나의 책임이 여러 메시지로 분할되는 것이 일반적이다. 

# 역할

어떤 객체가 수행하는 책임의 집합은 객체가 협력 안에서 수행하는 역할을 암시한다. 판사와 증인이라는 역할을 사용하면 어떤 특정 인물이 오더라도 여러 가지 협력을 모두 포괄할 수 있는 하나의 협력으로 추상화할 수 있다. 역할은 협력 내에서 다른 객체로 대체할 수 있음을 나타내는 일종의 표식이다. 하지만 역할을 대체할 수 있는 객체는 동일한 메시지를 이해할 수 있는 객체로 한정된다. 동일한 역할을 수행하는 객체들이 동일한 메시지를 수신할 수 있기 때문에 동일한 책임을 수행할 수 있다는 것은 매우 중요한 개념이다.

### 협력의 추상화

역할의 가장 큰 가치는 하나의 협력 안에 여러 종류의 객체가 참여할 수 있게 하면서 협력을 추상화할 수 있다는 것이다. 객체가 역할을 대체하기 위해서는 행동이 호환되어야 한다. 또한 객체는 역할에 주어진 책임 이외에 다른 책임을 수행할 수도 있다. 따라서 대부분 경우에 객체의 타입과 역할 사이에는 일반화, 특수화 관계가 성립하는 것이 일반적이다. 

역할의 대체가능성은 특정 행위의 호환성을 의미하고, 행위 호환성은 동일한 책임의 수행을 의미한다.

# 객체의 모양을 결정짓는 협력

객체지향의 가장 큰 선입견 두 가지는 다음과 같다.

- 시스템에 필요한 데이터를 저장하기 위해 객체가 존재한다.
- 객체지향이 클래스와 클래스 간의 관계를 표현한다.

중요한 것은 객체의 행동, 즉 책임이며, 데이터는 단지 재료일 뿐이다. 또한, 정적 측면이 아닌 협력에 참여하는 동적 객체가 중요하다.

# 협력을 따라 흐르는 객체의 책임

올바른 객체를 설계하기 위해서는 먼저 깔끔한 협력을 설계해야 한다. 즉, 설계에 참여하는 개체들이 주고받을 요청과 응답의 흐름을 결정해야 한다. 이렇게 결정된 것은 수행해야 하는 책임이 된다.

협력을 구상하는데 필요한 책임을 고안한 이후 책임을 수행하는데 필요한 객체를 선택한다. 특정 챔 임별로 각각의 객체에 할당하면서 할당한다. 그리고 이렇게 할당된 책임은 객체들이 외부에 제공하게 될 행동을 정의하게 된다. 이제 행동이 결정되었으니 각 객체가 필요로 하는 데이터가 정의가 가능하다. 그리고 이후에 클래스를 개발할 수 있게 된다.

협력에 필요한 책임을 결정하고 객체에게 책임을 할당하는 과정을 얼마나 합리적이고 적절하게 수행했는지가 객체지향 설계의 품질을 결정한다.

# 객체지향 설계 기법

책임 주도 설계는 협력에 필요한 책임들을 식별하고 책임을 할당하는 방식으로 애플리케이션을 설계한다. 디자인 패턴은 특정 문제를 해결하기 위해 이미 식별해 놓은 역할, 책임, 협력의 모음이다. 다음은 책임 주도 설계의 객체지향 시스템 설계 절차이다.

- 시스템이 사용자에게 제공해야 하는 기능인 시스템 책임을 파악
- 시스템 책임을 더 작은 책임으로 분할
- 분할된 책임을 수행할 수 있는 적절한 객체 또는 역할을 찾아 책임을 할당
- 객체가 책임을 수행하는 중에 다른 객체의 도움이 필요한 경우 이를 책임질 적절한 객체 또는 역할을 찾는다.
- 해당 객체 또는 역할에게 책임을 할당함으로써 두 객체가 협력하게 한다.

테스트 주도 개발은 테스트를 작성하는 것이 아니라 책임을 수행할 객체 또는 클라이언트가 기대하는 객체의 역할이 메시지를 수신할 때 어떤 결과를 반환하고 그 과정에서 어떤 객체와 협력할 것인지에 대한 기대를 코드의 형태로 작성하는 것이다. 즉, 테스트 주도 개발은 책임 주도 설계의 기본 개념을 따른다.