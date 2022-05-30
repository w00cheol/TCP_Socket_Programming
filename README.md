# 멀티 스레드, TCP 소켓 통신을 활용한 바카라 게임 구현

<!--
리눅스 운영체제를 사용하여 멀티 쓰레드 기반의 서버를 구현합니다.
서버는 클라이언트가 접속을 요청할 때마다 새로운 쓰레드를 생성합니다.
클라이언트는 게임 서버에 접속 하여 선택지를 얻습니다.
방 생성, 방 입장, 게임 종료가 있습니다.
방을 생성한 클라이언트는, 새로운 클라이언트의 입장을 기다립니다.
또다른 클라이언트가 방에 입장하면 게임이 시작됩니다.
게임이 종료된 후에는 로비로 돌아갑니다.
-->
![](https://user-images.githubusercontent.com/53927414/170966693-b45872ad-f392-4427-84eb-f10fba6f7d58.png)

* 서버를 열고 4명의 클라이언트가 접속합니다.

![](https://user-images.githubusercontent.com/53927414/170966796-ef59223d-22a6-4b84-b672-f9178aa8e714.png)

* pstree 명령어로 프로세스를 확인합니다.
* 현재 사용자가 4명이므로 서버 프로세스 thread_s 1개에 4개의 스레드가 존재합니다.
* 1개의 스레드를 가지는 클라이언트 프로세스 thread_c 4개에 각각 1개의 스레드가 존재합니다.

![](https://user-images.githubusercontent.com/53927414/170966815-75fffc70-9c1d-46a1-bd7d-1f5d88a6d830.png)

* 게임 상황입니다.
* woo와 alice가 1번 방에서 게임을 시작했습니다.
* alice의 패가 woo의 패보다 높아 게임을 승리했고 금액을 얻게 됩니다. 

![](https://user-images.githubusercontent.com/53927414/170966902-e4bda9b6-e4d0-473d-ba08-4dda6b3bb194.png)

* 이번에는 bob이 게임 방 생성을 요청합니다.
* 1번 방은 기존에 사용되었었지만 이미 클라이언트가 떠나고 비어있는 방이므로 또 다시 1번 방을 배정받습니다.
- woo는 1번 방에 입장합니다.
- 게임이 시작됐고 bob이 기권하였습니다.
- 양 선수가 베팅하지 않아 잔액은 미동입니다.

![](https://user-images.githubusercontent.com/53927414/170967011-a8e351ad-9b28-4af1-854d-a06bf04e195a.png)

* woo, bob, alice, trudy 모두가 게임을 종료한 상황입니다.
* 서버에 문구가 출력됩니다.

![](https://user-images.githubusercontent.com/53927414/170967091-2122f36e-d60a-4b8e-add1-045edc02ad54.png)

* server.txt 입니다.
* 각각 서버 스레드가 주요 내역을 적어 넣습니다.
