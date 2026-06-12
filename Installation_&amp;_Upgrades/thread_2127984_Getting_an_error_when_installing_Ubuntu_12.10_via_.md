---
title: "Getting an error when installing Ubuntu 12.10 via wubi"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by Dysautobot on 2013-03-21
Hey, this is my first post and my first shot at using Linux. This is part of the report log that I got. :confused:

```

03-21 16:42 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {776b64d8-e59d-11df-b91a-c08ace86a8e0} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {776b64d8-e59d-11df-b91a-c08ace86a8e0} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
03-21 16:42 DEBUG  TaskList: # Cancelling tasklist
03-21 16:42 DEBUG  TaskList: New task modify_bcd
03-21 16:42 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {776b64d8-e59d-11df-b91a-c08ace86a8e0} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {776b64d8-e59d-11df-b91a-c08ace86a8e0} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
03-21 16:42 DEBUG  TaskList: New task modify_bcd
03-21 16:42 DEBUG  TaskList: New task modify_bcd
03-21 16:42 DEBUG  TaskList: New task modify_bcd
03-21 16:42 DEBUG  TaskList: ## Finished modify_bootloader
03-21 16:42 DEBUG  TaskList: # Finished tasklist
```

---

### Post by bcbc on 2013-03-21
See this: [why-cant-i-install-ubuntu-or-wubi-on-a-dynamic-disk-the-request-isnt-suppor]("http://askubuntu.com/q/179215/14916")

---

