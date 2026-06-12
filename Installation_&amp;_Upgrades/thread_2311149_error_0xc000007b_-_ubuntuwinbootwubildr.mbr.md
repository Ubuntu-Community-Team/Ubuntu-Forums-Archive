---
title: "error 0xc000007b - \ubuntu\winboot\wubildr.mbr"
date: 2016-01-25
forum: Installation &amp; Upgrades
---

### Post by mich6 on 2016-01-25
Please note - I am a newbie, so be kind and use baby steps and explanations.

Struggled to get installation started on Dell Inspiron 3531 - got it started from within Windows 10 - clicked on wubi. Ubuntu is now on computer - when I start it offers me a choice of Windows and Ubuntu. Windows seems to work fine, but Ubuntu gives me the error and tells me Ubuntu cannot be loaded due to a missing file or file errors. I have read a thread that talks about gpt partitioning and that wubi's don't work with gpt partitioning, and suggests "post this from liveUSB flashdrive terminal  -  sudo parted/dev/sda unit s print" which, unfortunately, is all Greek to me...

I keep getting pulled in too many directions with too many options, and for a newbie it just encourages more mistakes. Can someone please tell me what to do, step by step so I can finally start with Ubuntu? I promise to work hard and learn fast and never be a newbie again...

---

### Post by siepo on 2016-01-25
Wubi is no longer supported and no longer recommended. Take a look at [https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

Do not expect completely explicit step-by-step instructions; there are just too many combinations of hardware and software. Just make sure you have good backups of everything you care about and know how to roll back a failed attempt.

---

### Post by ajgreeny on 2016-01-25
I don't think wubi will work with Windows 8, 8.1 or 10, so there is no point trying to go further with this query.

There is plenty of information on dual booting properly with separate partitions for the OSs, for example there is a comprehensive article at [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by grahammechanical on 2016-01-25
On the assumption that you have accepted that you should remove wubi.exe just like you would remove any other Windows application & then do a proper dual boot, there are a couple of things I would suggest that you consider.

1) Upgrade to Windows 10 before you install Ubuntu. This is one example of the problems you could get if you upgrade Windows 8 to Windows 10 after installing Ubuntu.

[http://ubuntuforums.org/showthread.php?t=2310792](http://ubuntuforums.org/showthread.php?t=2310792)

2) Use Windows utilities to defrag Windows and to resize Windows partitions to create space for Ubuntu

3) Follow the advice in this wiki page.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

