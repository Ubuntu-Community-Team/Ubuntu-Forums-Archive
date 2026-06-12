---
title: "ubuntu installation issues"
date: 2013-08-13
forum: Installation &amp; Upgrades
---

### Post by suresh_kumar2 on 2013-08-13
Hi everyone,

      I'm trying to install ubuntu using windows installer. However I'm unable to install the ubuntu 12.04 version....
I've mentioned the error report(the part which shows where exactly exception happens) below........

Could anyone please fix this issue......... Well thanks, in advance........:p


```
08-14 09:33 DEBUG  TaskList: ## Finished choose_disk_sizes
08-14 09:33 DEBUG  TaskList: ## Running create_preseed...
08-14 09:33 DEBUG  TaskList: ## Finished create_preseed
08-14 09:33 DEBUG  TaskList: ## Running modify_bootloader...
08-14 09:33 DEBUG  TaskList: New task modify_bcd
08-14 09:33 DEBUG  TaskList: ### Running modify_bcd...
08-14 09:33 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 9027.3515625 mb free ntfs)
08-14 09:33 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {79ff4099-8ac0-11e2-b41e-fdff9af8be3b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.
```


```
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {79ff4099-8ac0-11e2-b41e-fdff9af8be3b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.
```


```
>>stdout=
08-14 09:33 DEBUG  TaskList: # Cancelling tasklist
08-14 09:33 DEBUG  TaskList: New task modify_bcd
08-14 09:33 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {79ff4099-8ac0-11e2-b41e-fdff9af8be3b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.
```


```
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {79ff4099-8ac0-11e2-b41e-fdff9af8be3b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.
```


```
>>stdout=
08-14 09:33 DEBUG  TaskList: New task modify_bcd
08-14 09:33 DEBUG  TaskList: New task modify_bcd
08-14 09:33 DEBUG  TaskList: New task modify_bcd
08-14 09:33 DEBUG  TaskList: ## Finished modify_bootloader
08-14 09:33 DEBUG  TaskList: # Finished tasklist
```

---

### Post by coffeecat on 2013-08-13
Not a Forum Feedback thread.

*Thread moved to **Installation & Upgrades**.*

---

