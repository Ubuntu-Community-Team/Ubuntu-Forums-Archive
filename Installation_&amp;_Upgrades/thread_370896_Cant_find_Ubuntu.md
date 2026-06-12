---
title: "Cant find Ubuntu"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by c0d3m45t3r on 2007-02-26
I made a dual boot system (Win and Ubuntu 6.10)
I installed ubuntu, installed GRUB on (hd1) and everything went fine. So I reboot but there is no  trace of Ubuntu I automatically boot up Win. I restart again and hit F8 to select a different OS but Ubuntu is not on the list,  only Windows?!

Also I'm using a laptop for this if it matters..
Is there a cure for my problem?

Thank in advance!

(Will reinstalling grub help me here? [http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+reinstall]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+reinstall")

---

### Post by coxc24 on 2007-02-26
Did you install Windows after Ubuntu? If you did then it sounds like Windows has over written your MBR (Master Boot Record). If that is the case then there should be a post on here detailing how to restore Grub, i'm afraid I have never done it. The other option is to add Ubuntu to the Windows boot loader but that may not be easy/possible.

---

### Post by taurus on 2007-02-26
If you want to use GRUB as your bootloader, you probably need to install it to MBR--/dev/hda (hd0).

---

### Post by c0d3m45t3r on 2007-02-26
aha I see my mistake I installed GRUB on hd1 - cause I didn't know what the hell it is :D so need to reinstall grub and on hd0 this time, thank you.

---

