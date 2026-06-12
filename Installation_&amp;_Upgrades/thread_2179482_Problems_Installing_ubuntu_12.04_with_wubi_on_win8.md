---
title: "Problems Installing ubuntu 12.04 with wubi on win8"
date: 2013-10-08
forum: Installation &amp; Upgrades
---

### Post by akbarrkhan on 2013-10-08
from past 3 or 4 days i am really trying hard to install it but the problem is it starts downloading some file of 500 mb + from internet, but the downloading is so slow and after every 5 or 6 hours there is a black out in here so its always interrupted

i heard that there is a bug or some problem with windows 8 installer

can any body suggest me anything how to overcome this problem

---

### Post by grahammechanical on 2013-10-08
The Windows installer is not compatible with Windows 8. It is as simple as that.

[http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

Dual boot. But do your research. Many have problems installing with Windows 8 already on the hard disk. Here are two samples of what to expect:

[http://ubuntuforums.org/showthread.php?t=2179028](http://ubuntuforums.org/showthread.php?t=2179028)

[http://ubuntuforums.org/showthread.php?t=2170615](http://ubuntuforums.org/showthread.php?t=2170615)

Regards.

---

### Post by hakuna_matata on 2013-10-08
> but the problem is it starts downloading some file of 500 mb + from  internet, but the downloading is so slow and after every 5 or 6 hours  there is a black out in here so its always interrupted
IMHO slow downloads are not a wubi problem. Wubi works fine on win8 without [UEFI]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface") and [GPT]("http://en.wikipedia.org/wiki/GUID_Partition_Table"). Problem is that a lot of preinstalled win 8 systems use UEFI and GPT and [boot loader]("http://en.wikipedia.org/wiki/Boot_loader#Modern_boot_loaders") of wubi is not compatible.

If you use wubi on win8 with UEFI and GPT, you can download and run the windows part of installation. After reboot menu entry for Ubuntu runs an incompatible boot loader.

Try dual boot, but I am not sure if that solves your download problems.

---

