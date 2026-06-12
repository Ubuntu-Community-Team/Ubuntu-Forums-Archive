---
title: "Unable To install Ubuntu Alongside Windows"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by cybercity@localhost on 2011-04-02
I am unable to install ubuntu on my system. Lines of installation logs are.

P.S if thread has been posted in wrong section. :(



```
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
04-02 16:03 DEBUG  TaskList: # Cancelling tasklist
04-02 16:03 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
04-02 16:03 DEBUG  TaskList: New task check_iso
04-02 16:03 DEBUG  CommonBackend: Searching for local ISO
04-02 16:03 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-02 16:03 DEBUG  TaskList: New task get_metalink
04-02 16:03 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-02 16:03 DEBUG  TaskList: # Cancelling tasklist
04-02 16:03 DEBUG  TaskList: # Finished tasklist
```

---

### Post by fela on 2011-04-02
Please outline the steps you took. Where did this message appear?

The normal way to do it, is to run the Ubuntu live CD (after downloading and burning it), and choosing to resize the Windows partition to allow space for Ubuntu, and installing Ubuntu into the remaining space.

---

### Post by Rubi1200 on 2011-04-02
Try placing the wubi.exe and downloaded iso image in the same folder; then run wubi.exe again.

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
please post the contents of the entire log and wrap with code tags as before.

Another question, are your disks in Windows Basic or Dynamic and where are you trying to install Ubuntu to?

Thanks.

---

### Post by joaquinx on 2011-07-02
I had problems installing Ubuntu in this manner until I ONLY downloaded wubi and ran it. wubi then download the recent version of Ubuntu 11.04. Only then did it install inside windows. No installation CD nor iso file on disk. I simply let wubi to download a version of Ubuntu.

---

### Post by matiasw on 2011-07-06
I've now managed to run the wubi installer to completion, whereupon it asked for a reboot.

```

[B]07-05 17:58 INFO   root: Finished installation
07-05 17:58 INFO   root: Rebooting[/B]
7-05 17:58 DEBUG  TaskList: # Running tasklist...
07-05 17:58 DEBUG  TaskList: ## Running reboot...
07-05 17:58 DEBUG  TaskList: ## Finished reboot
07-05 17:58 DEBUG  TaskList: # Finished tasklist
07-05 17:58 DEBUG  root: application.quit
07-05 17:58 DEBUG  WindowsFrontend: frontend.quit
07-05 17:58 DEBUG  WindowsFrontend: frontend.on_quit
07-05 17:58 DEBUG  root: application.on_quit
07-05 17:58 INFO   root: sys.exit

```

After booting, I saw the Windows startup menu (the same one that offers to boot into safe mode after an unsafe power-off), with the options Windows 7 and Ubuntu. I chose Ubuntu, and got a line that read something like "the installation needs to finish" and a countdown. After the countdown, the computer hangs; the power stays on, the screen goes blank, and nothing happens.

---

### Post by Rubi1200 on 2011-07-06
Hi matiasw,
what you experienced was likely a graphics related issue.

These 2 posts explain things in more detail and how to find workarounds:
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)
[http://ubuntuforums.org/showthread.php?t=1613132&highlight=nomodeset](http://ubuntuforums.org/showthread.php?t=1613132&highlight=nomodeset)

---

### Post by boblizar on 2011-07-06
i am successfully running windows 7 x64 next to ubuntu 10.10 x64.....

i installed windows first to its own 100 gig partition, and then installed ubuntu on the other 900 gigs.  i used a windows 7 all in one dvd, and a ubuntu 10.10 x64 live cd.

i tried ubuntu first, and then windows, and windows did not like it and wanted to blast ubuntu off the drive.  dont install from windows, boot to the cd.

---

