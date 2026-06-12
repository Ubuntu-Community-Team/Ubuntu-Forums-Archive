---
title: "Cannot Load windows after recovering the grub"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by hedonist on 2007-10-31
Hi,
I had Ubuntu 7.04 Feisty on my PC. I then installed Windows Xp and recovered the grub using the steps given on the Ubuntu website. But when I re booted I did not see Windows listed in the Grub options at boot. So i read the documentation and made following entry in the menu.lst file

title  Microsoft Windows XP
#An entry for a Windows installation
#If you're reading this guide, you probably want this
root   (hd0,0)
savedefault
makeactive
chainloader +1

But at boot when I select this option I get Error 13: Invalid executable format.
I did fdisk and get the following output.:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          62      497983+  82  Linux swap / Solaris
/dev/sda2              63         677     4939987+  83  Linux
/dev/sda3             678        3269    20820240    b  W95 FAT32
/dev/sda4            3270        4865    12819870    b  W95 FAT32

Please help me its really urgent and important for me.
Thanks!

---

### Post by logos34 on 2007-11-01
xp system partition/c: drive is either sda3 or 4.  So try:

> title Microsoft Windows XP
#An entry for a Windows installation
#If you're reading this guide, you probably want this
**root (hd0,2)**
savedefault
makeactive
chainloader +1

or 'root (hd0,3)'

You also might want to change the boot flag (*) from swap (wrong) to windows.  Open gparted in linux>select xp partition>Partition>manage flags>mark 'boot'

---

