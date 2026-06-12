---
title: "Booting multiple OS xp ubuntu and 7"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by Alphamonkey on 2010-01-03
Hi, I have Ubuntu 9.10 karmic koala installed alongside windows xp on one of my hard drives. On a seperate hard drive I am plainning on installing windows 7 to test it out. I am wondering if there are any issues that I should be concerned with such as the Grub loader not recongnizing the windows 7 install cause its on a seperate physical drive or the windows 7 boot manager taking over instead of Grub. Thanks.

---

### Post by zvacet on 2010-01-04
Windows 7 will overwrite grub,and you will need to [reinstall grub.]("https://help.ubuntu.com/community/Grub2")

---

### Post by Alphamonkey on 2010-01-05
Thanks for the response thats good to know. Before I install 7 can you tell me how to install grub after 7 overwrites it I am still quite new to using linux. Thanks.

---

### Post by VastOne on 2010-01-05
> **Alphamonkey said:**
> Thanks for the response thats good to know. Before I install 7 can you tell me how to install grub after 7 overwrites it I am still quite new to using linux. Thanks.

Insert Ubuntu Live CD and restart system.

Open a terminal once in Ubuntu and do the following:-

sudo grub

find /boot/grub/stage1

Take not of whatever find states (hdx,x)

root (hdx,x)

setup (hdx)

quit

---

### Post by zvacet on 2010-01-05
@ **Alphamonkey**

I posted you link with instructions how to reinstall grub.

---

### Post by Dayofswords on 2010-01-05
xp, 7 and ubuntu

the middle child vista is left out in the cold:P

---

### Post by oldfred on 2010-01-05
VastOne posted the instructions for grub legacy (0.97). That is correct if your install of 9.10 is an upgrade from 9.04 and you did not separately update grub.
 If you have a new install of 9.10 you need to follow the instructions for grub2 (1.97beta4).

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Windows wants to install all its boot to one partition so you can choose which windows to use. When it does this it makes it immpossible for grub to separately boot each separately.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Vista/Win7 copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

