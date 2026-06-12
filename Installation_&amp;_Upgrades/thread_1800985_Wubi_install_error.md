---
title: "Wubi install error"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by jbills on 2011-07-09
I am trying to install wubi. However when I do I get an error about permissions. I am admin and have a ubuntu 11.04 iso in the same folder. That was one of the solutions I found in this forums. I have looked in my log and found the following:


```
07-09 20:19 DEBUG  WindowsBackend: Copying C:\Users\Taylor\AppData\Local\Temp\pyl8EA9.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-09 20:19 DEBUG  TaskList: ## Finished copy_installation_files
07-09 20:19 DEBUG  TaskList: ## Running get_iso...
07-09 20:19 DEBUG  TaskList: New task copy_file
07-09 20:19 DEBUG  TaskList: ### Running copy_file...
07-09 20:19 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
07-09 20:19 DEBUG  TaskList: # Cancelling tasklist
07-09 20:19 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
07-09 20:19 DEBUG  TaskList: New task check_iso
07-09 20:19 DEBUG  CommonBackend: Searching for local ISO
07-09 20:19 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Taylor\Downloads\ubuntu-11.04-desktop-amd64.iso
07-09 20:19 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Taylor\Downloads\ubuntu-11.04-desktop-amd64.iso
07-09 20:19 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
07-09 20:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
07-09 20:19 INFO   Distro: Found a valid iso for Ubuntu: C:\Users\Taylor\Downloads\ubuntu-11.04-desktop-amd64.iso
07-09 20:19 DEBUG  CommonBackend: Trying to use ISO C:\Users\Taylor\Downloads\ubuntu-11.04-desktop-amd64.iso
07-09 20:19 DEBUG  TaskList: New task check_iso
07-09 20:19 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-09 20:19 DEBUG  TaskList: New task get_metalink
07-09 20:19 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-09 20:19 DEBUG  TaskList: # Cancelling tasklist
07-09 20:19 DEBUG  TaskList: # Finished tasklist

```

At the bottom it checks the iso 2 times. The first time it succeeds the second time it fails. What is happening?

---

### Post by kommm on 2011-07-10
I am getting the exact same error. It keeps saying permission denied. I am the only user on the computer and am the admin, so I don't understand how permission can be denied.

---

### Post by westie457 on 2011-07-10
Hello.
 Are you trying to run the iso directly from your hard-drive?
If you are that is probably the cause of the errors. Try burning the iso to a cd using whatever burning program you have. Make sure it is burned as an iso so it will be bootable.

Hope this helps

---

### Post by bcbc on 2011-07-10
> **jbills said:**
> I am trying to install wubi. However when I do I get an error about permissions. I am admin and have a ubuntu 11.04 iso in the same folder. That was one of the solutions I found in this forums. I have looked in my log and found the following:

At the bottom it checks the iso 2 times. The first time it succeeds the second time it fails. What is happening?

You should post the whole file (or at least the whole section related to this particular failed install). It is usually a bad CD that is causing this (even if you have an ISO in the same folder, if there is also a bad CD it will find that and use that).
Hard to say since you didn't post the whole log :p (the error messages Wubi gives are usually unhelpful, unless you post the log)

Also see here for all installation options: [https://wiki.ubuntu.com/WubiGuide#Installation](https://wiki.ubuntu.com/WubiGuide#Installation)

---

### Post by jbills on 2011-07-10
I think i figured it out. I had an old ubuntu cd in the drive already. I think the iso which I burned to it was corrupted.

---

