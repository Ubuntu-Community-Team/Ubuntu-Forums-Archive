---
title: "installation problem &quot;access denied&quot;"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by alaa sam on 2011-01-22
hi every one I've just installed ubuntu and the installation suddenly stopped and showed me a message saying that access denied or something like that . I'm using now windows xp .
so can anybody tell me what should i do?

---

### Post by mikewhatever on 2011-01-22
Can we get a screenshot or at least the exact error message text.

---

### Post by nobilis.vir on 2011-03-16
Hia, 

I have the exact same problem.

I tried installing Ubuntu within Windows (for some reason my drive refuses to read the CD properly when booting into it) and right at the end of it, it fails.

Here's a link to a screenshot of it.
[http://i55.tinypic.com/2cypl39.jpg](http://i55.tinypic.com/2cypl39.jpg)

I went to the log and here are the last outputs of the installer:
03-16 15:40 DEBUG  TaskList: ## Finished copy_installation_files
03-16 15:40 DEBUG  TaskList: ## Running get_iso...
03-16 15:40 DEBUG  TaskList: New task copy_file
03-16 15:40 DEBUG  TaskList: ### Running copy_file...
03-16 15:45 DEBUG  TaskList: ### Finished copy_file
[B]03-16 15:45 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):[/B]
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
[B]IOError: [Errno 13] Permission denied
03-16 15:45 DEBUG  TaskList: # Cancelling tasklist
03-16 15:45 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):[/B]
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-16 15:45 DEBUG  TaskList: New task check_iso
03-16 15:45 DEBUG  CommonBackend: Searching for local ISO
03-16 15:45 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-16 15:45 DEBUG  TaskList: New task get_metalink
03-16 15:45 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-16 15:45 DEBUG  TaskList: # Cancelling tasklist
03-16 15:45 DEBUG  TaskList: # Finished tasklist


Could I please get some help on this?

Will be much appreciated.

Kind regards,
nobie

---

### Post by Rubi1200 on 2011-03-16
Try placing the wubi.exe and downloaded iso image files in the same folder and then run wubi.exe again.

---

### Post by nobilis.vir on 2011-03-16
The thing is, I ran it from the CD, but will put them in a folder on my drive and try again.

Thanks for the suggestion :)

---

### Post by matiasw on 2011-07-02
I've got this issue installing Ubuntu 11.04 in Win7 x64. Thing is, I've already downloaded the ISO and placed it alongside wubi.exe, and it's detected by wubi, but the installation still fails. I'm running wubi as Administrator, and have also tried using the hidden Administrator account.

```

07-02 20:56 DEBUG  TaskList: ## Finished copy_installation_files
07-02 20:56 DEBUG  TaskList: ## Running get_iso...
07-02 20:56 DEBUG  TaskList: New task copy_file
07-02 20:56 DEBUG  TaskList: ### Running copy_file...
**07-02 20:59 ERROR  TaskList: [Errno 13] Permission denied**
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
07-02 20:59 DEBUG  TaskList: # Cancelling tasklist
07-02 20:59 DEBUG  TaskList: New task check_iso
07-02 20:59 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
**IOError: [Errno 13] Permission denied**
07-02 20:59 DEBUG  CommonBackend: Searching for local ISO
07-02 20:59 DEBUG  Distro:   checking Ubuntu ISO C:\Users\wavesum\Downloads\installation.iso
07-02 20:59 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\wavesum\Downloads\installation.iso
07-02 20:59 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
07-02 20:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
**07-02 20:59 INFO   Distro: Found a valid iso for Ubuntu: C:\Users\wavesum\Downloads\installation.iso**
07-02 20:59 DEBUG  CommonBackend: Trying to use ISO C:\Users\wavesum\Downloads\installation.iso
07-02 20:59 DEBUG  TaskList: New task check_iso
07-02 20:59 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-02 20:59 DEBUG  TaskList: New task get_metalink
07-02 20:59 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
**Exception: Cannot download the metalink and therefore the ISO**
07-02 20:59 DEBUG  TaskList: # Cancelling tasklist
07-02 20:59 DEBUG  TaskList: # Finished tasklist

```

---

### Post by Rubi1200 on 2011-07-02
Hi matiasw,
it doesn't help us here if you attach your posts to other threads because then we don't know where to look to help you. 

I have already answered in the other thread where you posted.

Please start a new thread if you want more attention for your problem.

Thanks.

---

### Post by matiasw on 2011-07-06
> **Rubi1200 said:**
> Hi matiasw,
it doesn't help us here if you attach your posts to other threads because then we don't know where to look to help you. 
I have already answered in the other thread where you posted.


You're right; let's keep the discussion in [the other thread]("http://ubuntuforums.org/showthread.php?p=11005537#post11005537"). :popcorn:

---

