---
title: "No os found after ubuntu 10.04 fresh install"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by kc2dws on 2011-09-27
Hello all.

 I did a clean install of Ubuntu 10.04. The install went fine, I used the whole disk. The first two times I tried to boot I received no operating system found. The third attempt I received a screen that said grub (gnu grub version 1.98).

 The live CD boots to desktop and all parameters look as expected , video sound ram. Also there should have been a mbr with windows xp sp3.

 Any ideas why system is not finding the system.

Thank you for your time
Kevin

---

### Post by dino99 on 2011-09-27
you scared me when said "i used the whole disk", i hope you dont format the whole hdd and lost xp3

standard install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

you might either have not set the partition bootable before formatting, or hdd have issue like cluster damaged.

note: some brand like acer, dell and others put some hidden partition (tatooed) that even format cant remove, only low formatting with seagate tool can do the job. These hidden partition can take place of mbr and disturb the bootloader.

---

### Post by kc2dws on 2011-09-27
Thank for the reply.

 You were right, The hard drive has gone bad. After replacing it and reinstalling to a new one thing are now working. Didn't mean to scare you. I only put a 30gb hard drive in.

thank you

kevin

---

