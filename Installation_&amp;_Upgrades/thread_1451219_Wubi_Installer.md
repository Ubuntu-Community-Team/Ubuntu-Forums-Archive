---
title: "Wubi Installer"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by bingo23 on 2010-04-10
Is there a link anywhere to download the 10.4 version with the wubi installer - cannot seem to find one that existed last week

---

### Post by beta.tester on 2010-04-10
[B]Hi

Just spotted this entry on Ubuntu's site, I hope it helps:

Wubi as included on the ISO images is unable to enter its second stage of installation, so you will not be able to install inside Windows using just an ISO image in this beta release. As a workaround, users who are installing the Ubuntu Desktop Edition can download the stand-alone version of wubi from [http://releases.ubuntu.com/10.04/wubi.exe](http://releases.ubuntu.com/10.04/wubi.exe)  which includes the fix for this bug. This bug will be fully addressed for 10.04 LTS Beta 2. (541607) 

Kind regards    john

[/B]

---

### Post by osod88 on 2010-04-10
Hi, 
I also have a problem with the wubi installer. I'm trying to install 10.04 beta2 netbook edition, on a windows 7 32 bit OS, but I get the following error, from the logfile:
```
04-10 14:27 DEBUG  WindowsBackend: Copying C:\Users\ben\AppData\Local\Temp\pyl11AC.tmp\data\images\Ubuntu Netbook Edition.ico -> C:\ubuntu\Ubuntu Netbook Edition.ico
04-10 14:27 ERROR  TaskList: [Errno 2] No such file or directory: 'C:\\Users\\ben\\AppData\\Local\\Temp\\pyl11AC.tmp\\data\\images\\Ubuntu Netbook Edition.ico'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 162, in copy_installation_files
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\Users\\ben\\AppData\\Local\\Temp\\pyl11AC.tmp\\data\\images\\Ubuntu Netbook Edition.ico'
04-10 14:27 DEBUG  TaskList: # Cancelling tasklist
04-10 14:27 DEBUG  TaskList: # Finished tasklist
04-10 14:27 ERROR  root: [Errno 2] No such file or directory: 'C:\\Users\\ben\\AppData\\Local\\Temp\\pyl11AC.tmp\\data\\images\\Ubuntu Netbook Edition.ico'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 162, in copy_installation_files
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\Users\\ben\\AppData\\Local\\Temp\\pyl11AC.tmp\\data\\images\\Ubuntu Netbook Edition.ico'

```
I tried running it as administrator but it didn't help. Thanks for any suggestions.
UPDATE 1:
I was thinking of installing ubuntu 9.10 netbook remix with wubi then dist-upgrade it as a workaround but this approach also failed...the error was: "Cannot download the metalink and therefore the ISO". I used rev. 170 this time.

---

