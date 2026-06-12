---
title: "Tri boot Ubuntu XP and Vista"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by aren55555 on 2007-05-24
Here's the problem:

Currently I have XP installed on one of my drives (C: 260GB). That same drive is partitioned for Vista giving vista V: 60GB. I have another hard drive (Z: 320 GB) with no OS installed; but contains tons of music pics, videos, etc. When my current setup boots up the vista bootloader lets me choose between Vista or XP. What I want to do is:
Install Ubuntu on the Z drive, while still allowing use of Vista and XP.

Furthermore, i was wondering if it was possible to do all the partitiopning work before the Ububntu instal in xp using partition magic 8. Also if this is possible how? and ext2 or ext3 for Ubuntu? FAT32 for sharing files?

One more question what is the Linux swap for?



If more info is needed just ask

A few links I found during research:
[http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php](http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php)
[http://neosmart.net/forums/index.php?gettopic=391](http://neosmart.net/forums/index.php?gettopic=391)
[http://forums.ngemu.com/software-discussion/89276-tri-booting-windows-xp-windows-vista-ubuntu-7-04-feisty-fawn.html](http://forums.ngemu.com/software-discussion/89276-tri-booting-windows-xp-windows-vista-ubuntu-7-04-feisty-fawn.html)
[http://www.brandonking.net/blog/2006/11/tri-boot-winxp-windows-vista-ubuntu.html](http://www.brandonking.net/blog/2006/11/tri-boot-winxp-windows-vista-ubuntu.html)

---

### Post by apunc1 on 2007-05-25
> **aren55555 said:**
> 
One more question what is the Linux swap for?



swap is a small hard disk partiton that your os can use as memory if it runs out of ram memory
[http://en.wikipedia.org/wiki/Swap_space](http://en.wikipedia.org/wiki/Swap_space)

ext3 is the appropriate format for your Ubuntu partition. FAT32 can be used to share files between linux and windows. or you can use FS-Drive which is a small program that allows Windows to read from and write to Ext3 partitions. So you won't need the fat32 partiton, just ext3for ubuntu, ext3 for shared data, ntfs for windows.

i've never worked with two hard drives. if you search the forums here or google you can find guides to help with that.

---

