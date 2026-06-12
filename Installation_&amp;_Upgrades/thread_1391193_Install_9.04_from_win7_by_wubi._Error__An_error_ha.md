---
title: "Install 9.04 from win7 by wubi. Error  An error has occurred setting the element data"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by rachzhang on 2010-01-26
[SIZE=2]Hello all,

I tried to install ubuntu 9.04 from wubi in windows 7 ultimate today. But it failed. I met a problem when installing: ***An error has occurred setting the element data. The request is not supported.***

The detailed information in installation log file is:[/SIZE]
>>stdout=
01-26 13:29 DEBUG  TaskList: # Cancelling tasklist
01-26 13:29 DEBUG  TaskList: New task modify_bcd
01-26 13:29 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {d29666c7-0a4d-11df-a945-002268e2b352} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {d29666c7-0a4d-11df-a945-002268e2b352} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.

[SIZE=2]I tried to use bcdedit /set <GUID> device partition=I: manually, but still have the same error.

Anyone can tell me how to fix it? 

Thanks very much![/SIZE]

---

### Post by danish_123786 on 2010-02-21
hey even i am facing the same problem with same error message..please some help...
thanks
 
 
 
>>command=C:\Windows\System32\bcdedit.exe /set {ffe37e88-1f94-11df-8c57-ec021f456b2b} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.

>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 629, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {ffe37e88-1f94-11df-8c57-ec021f456b2b} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.

---

### Post by MattRoxors on 2010-03-30
I get the same error with 9.10 when installing from windows 7, either of you two had any luck?

---

