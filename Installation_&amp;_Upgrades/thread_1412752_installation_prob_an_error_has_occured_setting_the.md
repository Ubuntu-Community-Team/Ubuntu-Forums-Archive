---
title: "installation prob an error has occured setting the element data"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by danish_123786 on 2010-02-21
Hi,
i m not able to install ubuntu 9.10 inside windows, the error which i m getting is depicted below.....kindly help me i will be eagerly wait for the solution...
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

