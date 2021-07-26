# WebSocket

출처 



### 정의(위키백과)

- 하나의 TCP 접속에 전이중 통신 채널을 제공하는 컴퓨터 통신 프로토콜

  미디어 서버와 WebRTC 연결을 위한 메시지 송수신 기능을 구현할 수 있음



Websocket 기능을 위해서는 SockJS 와 Stomp 의 개념과 사용 방법을 알아봐야함



### SockJS

SockJS 는 WebSocket 스펙을 지원하지 않는 브라우저에서도 Polling 으로 대체하여 Frontend, Backend 간의 연결 및 메시지 송수신 기능을 지원해주는 WebSocket Polyfill 라이브러리

간단한 예시

```vue
<script src="https://cdn.jsdelivr.net/npm/sockjs-client@1/dist/sockjs.min.js"></script>

 var sock = new SockJS('https://mydomain.com/my_prefix');
 sock.onopen = function() {
     console.log('open');
     sock.send('test');
 };

 sock.onmessage = function(e) {
     console.log('message', e.data);
     sock.close();
 };

 sock.onclose = function() {
     console.log('close');
 };
```



### Stomp

Stomp 는 단순 텍스트 기반의 메시지 프로토콜로 Websocket 같은 양방향 통신 프로토콜에 사용

통신 연결 및 해제, 메시지 브로커를 통해 클라이언트가 특정 Topic에  Subscribe 가능하게 함, 해당 Topic으로 다른 클라이언트가 메시지를 Send하면, 해당 Topic에 Send 된 메시지를 해당 Topic 에 Subscribe 한 클라이언트를 모두가 받을 수 있게 함
