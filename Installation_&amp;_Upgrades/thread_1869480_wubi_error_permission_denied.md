---
title: "wubi error permission denied"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by glenngds on 2011-10-25
the following is the last few lines in the wubi log file:

10-25 18:11 ERROR  TaskList: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'
10-25 18:11 DEBUG  TaskList: # Cancelling tasklist
10-25 18:11 DEBUG  TaskList: # Finished tasklist
10-25 18:11 ERROR  root: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'


Funny but E:\ on my computer is a internal, built in camera memory slot and is therefore non-existent unless a camera memory device is plugged into it.  I guess there is no work arounds for this mistake by the developer of wubi until this bug is reported and solved.

---

### Post by bcbc on 2011-10-26
See this bug [lpbug]862003[/lpbug]. The install is likely fine and ready to go first time you reboot.

See also [this]("http://ubuntu-with-wubi.blogspot.com/2011/10/oneric-ocelot-1110-released.html") which discusses the difference between the preinstalled image (which you have) and the usual wubi install method.

---

