### Table of Contents
[Stack](#stack)  
[Queues](#queues)  
[QueueArray](#queuearray) (array based queue)

---

#### Stack
#### Queues

요즘에는 우리가 자주 접하는 문화 생활을 위해 줄을 서는 일이 현저히 줄었다. 
스마트폰의 앱을 통해서 식당을 예약하고 영화를 예매한다. 

오히려 이제는 희귀한 서비스나 제품들을 위해 우리는 기꺼이 줄을 선다.

S 커피 체인점의 굿즈를 구매하기 위해 그리고 제주도의 소문난 Y 돈까스를 먹기 위해 우리는 시간을 내어 줄을 선다.

여기서 줄을 서는 행위는 Queue 의 구조와 아주 유사하다.
먼저 도착한 사람 순서대로 서비스를 받을 수 있듯이, Queue 에서도 먼저 도착한 순서대로 제거될 수 있다. 

---
Queue 는 Array, Doubly linked list 등 다양한 방법으로 구현이 될 수 있다. 

구현 방법은 다양하나 이 구현체들이 행하는 행위들은 아주 간단하다. 
```
- enqueue
데이터를 삽입하고
- dequeue
데이터를 제거한다.
```

이 주요 행위들을 제외하고, 부수적으로 Queue 가 비어 있는지, 첫번째 값은 무엇인지 들여다보는 등의 행위들이 포함될 수 있다. 

---

##### Protocol
위에 언급된 Queue 의 기본 오퍼레이터들을 갖는 프로토콜이다. 
```swift
public protocol Queue {
	associatedType Element
	// Key methods
	mutating func enqueue(_ element: Element) -> Bool
	mutating func dequeue() -> Element?
	// Supplementary methods
	var isEmpty: Bool { get }
	var peek: Element? { get }
}
```

##### QueueArray

Queue 를 구현하는 방법 중 가장 간단하다. 
Array 를 Data 컨테이너로써 선언하고 Array 의 메소드를 이용해 Queue 를 조작할 수 있다.

###### QueueArray 의 기본 골격
```swift
public struct QueueArray<T>: Queue {
	private var array: [T] = []
	public init() {}
}
```

###### Enqueue · Dequeue
```swift
public mutating func enqueue(_ element: T) -> Bool {
	array.append(element)
	return true
}
public mutating func dequeue() -> T? {
	isEmpty ? nil : array.removeFirst()
}
```

###### Pros and Cons
개발자들이 친숙한 Array 로 구현했기 때문에 아주 쉽게 구현될 수 있다.


##### QueueLinkedList
##### QueueRingBuffer

