---
title: "install fails &quot;backend object has no attribute &quot;iso-path&quot;"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by palloy on 2011-11-01
I downloaded Ubuntu 11.10 and put it on a USB stick.
I successfully installed it to HDD, messed about, crashed it, etc.
Now I am trying a clean install to SSD partition of 10 GB.
Everything went as before until the countdown clock reached zero, then I got
"Windows Backend object has no attribute 'iso-path' - see log for details.
It's done it three times now. (Formatting in between)

The end of the log says
======
[FONT=Courier New]11-01 17:20 DEBUG  TaskList: New task check_iso
11-01 17:20 DEBUG  TaskList: ### Running check_iso...
11-01 17:20 DEBUG  CommonBackend: Checking Y:\ubuntu\install\installation.iso
11-01 17:20 DEBUG  Distro:   checking Ubuntu ISO Y:\ubuntu\install\installation.iso
11-01 17:20 DEBUG  Distro:     [COLOR=Red]wrong size: 8094031872 > 900000000[/COLOR]
11-01 17:20 DEBUG  TaskList: ### Finished check_iso
11-01 17:20 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
11-01 17:20 DEBUG  TaskList: # Cancelling tasklist
11-01 17:20 DEBUG  TaskList: # Finished tasklist
11-01 17:20 ERROR  root: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
=======

Note the bit in red, 8 billion > 900 million.
The installation.iso is indeed 8 billion bytes, I imagine it is going to be root.disk isn't it. It is the 900 million that is wrong, should be 9 billion right ?

I've check the SSD partition for errors and its fine.


[/FONT]

---

### Post by bawbawbiscuit on 2011-11-12
I have the same problem as well

---

### Post by oneone687 on 2011-11-15
Me too I have same problem

---

### Post by Rubi1200 on 2011-11-15
Common causes could be an interrupted download, failed md5sum, or bad burn to CD.

> The easiest way to install Wubi is without burning anything. Just place  the downloaded desktop CD ISO in your downloads folder along with  Wubi.exe and run wubi.exe from there. Make sure you also remove any  other CD's or USB's that contain Ubuntu from your computer as wubi will  find them and use them instead. That includes ISO files saved in the  root of any drive. (courtesy of forum member bcbc).

---

