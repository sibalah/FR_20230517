# Github README 페이지 만들기 과제 20233071 장원종

## top 명령어

top's mean : table of processes CPU와 메모리 이용에 관한 정보를 표시.

![sdf](https://github.com/ImBestintheWorld/FR_20230517/assets/133841660/c88bf9e1-c1cf-46f3-9bbf-9a8a1c26ede6)

윗 사진과 같이 상단에는 요약영역이 존재한다 

요약영역은 전체 프로세스가 OS에 대해서 리소스를 어느정도 차지하고 있는 지 보여준다.

요약영역은 
System time, Uptime, User
Load Average
Tasks
CPU
Memory 구성되어 있으며 

윗 사진을 분석해서 설명하겠다

![OMG](https://github.com/ImBestintheWorld/FR_20230517/assets/133841660/a8b84de7-ba6d-41eb-a253-d1e745f9592a)

* ###  System time, Uptime, User
  * top 16:58:55 up - 시스템의 현재 시간을 표시
  * 7days, 1:15 - 서버 구동 시간 표시
  * 2 users - 현재 접속중인 유저 세션 수 표시

* ###  Load Average
  * CPU Load의 이동 평균을 표시 (CPU Load는 CPU가 수행하는 작업의 양)
  * 왼쪽부터 1분, 5분 ,15분에 대한 평균값이다

* ###  Tasks
  * Task는 현재 프로세스들의 상태를 나타내주는 영역
  * Total, running, sleeping, stopped, zobies로 구성
  * Total - 전체 프로세스 표시 
  * running - 구동중인 상태인 프로세스
  * sleeping - 대기상태인 프로세스
  * stopped - 종료된 프로세스
  * zombies - 좀비상태인 프로세스 
  
  >좀비상태 - 프로세스가 종료되고 리소스는 모두 회수되었지만, 시스템 프로세스 테이블에 남아있는 defunct 상태의 프로세스를 말한다.
* ###  %Cpu(s)
  * CPU가 어떻게 사용되고 있는가, CPU 사용율을 표시하는 영역
  * us : 프로세스의 유저 영역에서의 CPU 사용률
  * sy : 프로세스의 커널 영역에서의 CPU 사용률
  * ni : 프로세스의 우선순위(priority) 설정에 사용하는 CPU 사용률
  * id : 사용하고 있지 않는 비율
  * wa : IO가 완료될때까지 기다리고 있는 CPU 비율
  * hi : 하드웨어 인터럽트에 사용되는 CPU 사용률
  * si : 소프트웨어 인터럽트에 사용되는 CPU 사용률
  * st : CPU를 VM에서 사용하여 대기하는 CPU 비율
  
* ###  KiB Mem, KiB Swap
  * 메모리 영역 디스크를 메모리 처럼 이용하는 Swap
  * total : 총 메모리 양
  * free : 사용가능한 메모리 양
  * used : 사용중인 메모리 양 
>buff/cache는 IO와 관련되어 사용되는 버퍼에 사용되는 메모리를 말합니다

![Newjeans](https://github.com/ImBestintheWorld/FR_20230517/assets/133841660/408566dc-1bba-45fe-8e0c-a11c7b2d137d)

상단에 있는 대부분의 정보들은 설명을 마치고, 하단에 있는 디테일 영역입니다.

* ### PID
  * PID는 프로세스 ID이며 프로세스를 구분하기 위한 겹치지않는 고유한 값입니다.
* ### USER
  * 해당 프로세스를 실행한 USER 이름 또는 효과를 받는 USER의 이름입니다. 
* ### PR & NI   
  * PR : 커널에 의해서 스케줄링되는 우선순위입니다.
  * NI : PR에 영향을 주는 nice라는 값입니다.
* ### VIRT, RES, SHR, %MEM 
  * VIRT : 프로세스가 소비하고 있는 총 메모리입니다. 프로그램이 실행중인 코드, heap, stack과 같은 메모리, IO buffer 메모리를 포함합니다.
  * RES : RAM에서 사용중인 메모리의 크기를 나타냅니다
  * SHR : 다른 프로세스와의 공유메모리(Shared Memory)를 나타냅니다.
  * %MEM : RAM에서 RES가 차지하는 비율을 나타냅니다.

> *top 명령어는 굉장히 정보량이 많고 파면 팔 수록 계속 정보들이 나오는 명령어 이였습니다 하지만 하드웨어의 심장이라고 할 수 있는 부품들의 이용 정보들을 자세하게 알 수 있어 " 잘 안다면 " 매우 유용할 것이라고 생각됩니다.*

## ps 명령어

ps's mean : ps는 process status의 줄인말, 현재 실행중인 프로세스 목록과 상태를 출력하여 보여주는 기능한다

>*윈도우 작업관리자와 유사하다고 하는데... 본인은 작업 끝내기밖에 안 써서 잘 모르겠다.*

ps는 옵션이 다양하며, 그 중에 

* ps aux 
  * 시스템의 동작중인 모든 프로세스를 소유자 정보와 함께 다양한 정보를 출력
* ps -ef 
  *  시스템에 동작중인 모든 프로세스를 자세하게 출력
* ps -el 
  * ef 명령에서 보이지 않았던 많은 정보들이 출력 

이 위에 말고도 기본명령어로는 

| Options | Description |
| --- | --- |
| -A | 모든 프로세스를 출력 |
| -r | 현재 실행 중인 프로세서를 출력 |
| -f | full 포맷 출력 |
| -l | 긴 포맷 출력 | 
| -M | 64비트 프로세스 출력 |
| -u | 프로세스 소유자를 기준으로 출력하는 기능들이 존재 |

## jobs 명령어 

jobs 명령어란? jobs 명령어는 백그라운드로 실행된 프로그램이나 Ctrl + z를 입력하여 실행한 프로그램에 대해서 확인하는 명령어이다.

**jobs 도 다양한 옵션들이 존재한다**


| Options | Description |
| --- | --- |
| -p | 모든 프로세스를 출력 |
| -l | 현재 실행 중인 프로세서를 출력 |
| -s | full 포맷 출력 |
| -r | 긴 포맷 출력 | 


 <img width="243" alt="2023-05-18" src="https://github.com/ImBestintheWorld/FR_20230517/assets/133841660/48378fa0-d293-435e-95ba-4892c26b13ab">
 
 jobs으로 출력되는  백그라운드의 작업의 상태값이다.
 
| Status | Description |
| --- | --- |
| Running | 작업이 계속 진행중임 |
| Done | 작업이 완료되어 0을 반환 |
| Stopped | 작업이 일시중단 |

## kill 명령어 

kill's mean : 프로세스에 시그널을 보내는 명령어
>*kill인 이유는 어떤 시그널을 보낼 지 지정하지 않으면 기본적으로 특정 시그널을 보내는데 특정 시그널이 프로그램 종료이다*

| Options | Description |
| --- | --- |
| -9 | 프로세스 아이디 직접 지정하여 종료시 사용된다 |
| -l | 신호로 사용할 수 있는 신호 이름들을 보여준다 |

+ 시그널을 보낼때는 kill -(보낼 시그널)PID 사용한다 kill PID 특정 시그널을 보낸다.

> 이것으로 마치겠습니다 감사합니다.
![IMG_7881](https://github.com/ImBestintheWorld/FR_20230517/assets/133841660/8ec45149-9121-4938-957a-349ac7ea1c65)


