---
title: "problems reinstalling grub mbr 9.1"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by dafuzzbudd on 2010-01-31
reinstalling xp killed my dual boot. i tried reinstalling grub from the CD.  after doing sudo grub then the "find /boot/grub/stage1" i've been trying to follow people's instructions for reinstalling grub.  it then gives me error 15 "file not find".  

doing "sudo fdisk -l"

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5992    48130708+   7  HPFS/NTFS
/dev/sda2            5993        7295    10466347+   f  W95 Ext'd (LBA)
/dev/sda5            5993        7295    10466316   83  Linux

What do I need to do in order to make this work correctly?  I cannot access my folders with saved files in order to just reinstall. 

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by oldfred on 2010-01-31
The instructions you linked to are for grub legacy. If you did a clean install of Karmic you now have grub2(grub1.97beta4)

If you did get it to install grub legacy you may have both and that is an even bigger problem.

Standard reinstall:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Alternative ways to install:
Three ways  note chroot is just to reinstall grub.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

See this thread &  post #10 if you have both grub's installed
[http://ubuntuforums.org/showthread.php?t=1350856](http://ubuntuforums.org/showthread.php?t=1350856)

---

### Post by dafuzzbudd on 2010-02-01
yay! that's what i was looking for and couldnt find. easy fix.

got me into ubuntu on sda5, then i did grub-update and redetected xp. all is well

---

