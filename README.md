
저는 이 프로젝트를 x64dbg 만을 사용하여 리버싱하였습니다. 

우선 Keyauth 에 불필요한 설정들을 모두 꺼줍니다. 
![image](https://github.com/uniopwe2001/Nomu-weak-point/assets/61898884/a564afa9-6b9b-41d7-9154-a5f1cd9c495a)

ScyllaHide 는 Anti Anti debugging 관련 plugin 입니다. 

scyllahide 의 모든 설정을 off 로 해둔 뒤 디버깅을 해주면 
![image](https://github.com/uniopwe2001/Nomu-weak-point/assets/61898884/bfa7a585-d4af-44bc-8d29-db1c3ea59e12)
이렇게 성공적으로 디버깅이 되는 것을 볼 수 있습니다. 

그 후 user module 에 있는 string 을 검색해주면 대략적으로 
keyauth 에서 제공하는 
name, ownerid, scret, version 등을 확인할 수 있습니다. 

![image](https://github.com/uniopwe2001/Nomu-weak-point/assets/61898884/91982120-dd73-47c8-9da3-1defe5d3dfe7)

제가 리버싱한 프로그램에서는 double 로 보이네요.

keyuath 는 rsa 와 ssl 을 이용하고 있고 또한 skcrypt 라는 문자열 암호화가 기본적으로 들어가있으니 
쉽게 리버싱할 수는 없습니다. 
하지만 loader 에 포함되어있는 name 중 Login 관련 된 내용이 매우 잘 나와있으니 
login 함수가 어디서 call 되는지, jne 혹은 je 로 jmp 시키는 곳에서 어떤 동작을 하는지 확인하시면 쉽게 리버싱 하실 수 있습니다. 
