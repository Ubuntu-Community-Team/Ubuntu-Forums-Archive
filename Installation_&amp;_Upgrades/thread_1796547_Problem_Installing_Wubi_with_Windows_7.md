---
title: "Problem Installing Wubi with Windows 7"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by ynsairam on 2011-07-03
Hi there, 
I am facing a problem installing wubi in my laptop that had a preinstalled Windows 7 home premium 64 bit. 

The error is some thing like this
07-03 19:58 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 98530.3046875 mb free ntfs)
07-03 19:58 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {df950028-72e0-11df-842f-a0ec9a1f28fb} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {df950028-72e0-11df-842f-a0ec9a1f28fb} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
07-03 19:58 DEBUG  TaskList: # Cancelling tasklist
07-03 19:58 DEBUG  TaskList: New task modify_bcd
07-03 19:58 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {df950028-72e0-11df-842f-a0ec9a1f28fb} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {df950028-72e0-11df-842f-a0ec9a1f28fb} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.

Can some one please help me ? 
Thanks
Nutan

---

### Post by bcbc on 2011-07-04
Most likely you are using dynamic drives. These are a Windows only logical volume manager and are not supported by Ubuntu.

You could install to an external drive; otherwise you'll have to get rid of the dynamic drives.

To check, open "Disk Management" and look at the volume type.

---

