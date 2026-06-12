---
title: "wubi.exe showing permission denied error"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by n.arrow001 on 2011-08-16
Hello Guys!
I am having this serious problem.

Firstly I am relatively very new to Ubuntu.
I am having a CD containing Ubuntu 10.10
It installed the Os on my Pc last month finely.

I (due to some reasons uninstalled that previous installation) now when I run it. it stops mid way and says permission denied check some log file.
Please help me I am going nuts.


One more thing

when tried to install 10.04.3 desktop then too it showed same error

---

### Post by shubham1 on 2011-08-16
what were the reasons you un installed ubuntu does it causes the same probelm or other.

---

### Post by n.arrow001 on 2011-08-16
Hello Guys

I m getting this again and again...please do some help



08-16 19:40 DEBUG  CommonBackend: Searching for local CD
08-16 19:40 DEBUG  Distro:   checking whether C:\Users\mishra\AppData\Local\Temp\pylAAFD.tmp is a valid Ubuntu Netbook CD
08-16 19:40 DEBUG  Distro:     does not contain C:\Users\mishra\AppData\Local\Temp\pylAAFD.tmp\casper\filesystem.squashfs
08-16 19:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-16 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-16 19:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-16 19:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-16 19:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-16 19:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-16 19:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
08-16 19:40 INFO   Distro: Found a valid CD for Ubuntu Netbook: G:\
08-16 19:40 DEBUG  TaskList: New task copy_file
08-16 19:40 DEBUG  TaskList: ### Running copy_file...
08-16 19:45 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
08-16 19:45 DEBUG  TaskList: # Cancelling tasklist
08-16 19:45 DEBUG  TaskList: New task check_iso
08-16 19:45 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
08-16 19:45 ERROR  TaskList: coercing to Unicode: need string or buffer, NoneType found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 481, in use_iso
  File "\lib\ntpath.py", line 282, in isfile
TypeError: coercing to Unicode: need string or buffer, NoneType found
08-16 19:45 DEBUG  TaskList: # Cancelling tasklist
08-16 19:45 DEBUG  TaskList: # Finished tasklist




thank you in advance

---

### Post by bcbc on 2011-08-16
There is a problem with the CD in G: ... a bad burn? Please post the whole log between [CODE][[SIZE="1"] [/SIZE]/CODE] tags next time. (And only one thread for help)

---

### Post by Elfy on 2011-08-16
Merged. Please do not post duplicates, it dilutes community effort.

---

