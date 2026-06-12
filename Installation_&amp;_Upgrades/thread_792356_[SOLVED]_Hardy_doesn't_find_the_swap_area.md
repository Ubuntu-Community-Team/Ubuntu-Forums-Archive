---
title: "[SOLVED] Hardy doesn't find the swap area"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by JC Cheloven on 2008-05-12
Hi, I don't know really where to post this. Perhaps not an installation problem. I didn't find anything similar in the forums. Anyway:

Hardy does not 'see' the swap area in my laptop Toshiba A50 (see specs below). When I type 
```
top
```
It says at the 5th line: Swap 0k total, 0k used, 0k free, 296780k cached 
I would expect something as 1400000k of total swap, as I have a swap partition about 1.4 Gb. It seems to be Hardy-specific, as the expected size of swap is displayed ok in Gutsy on the same computer (I have dual boot xp-gutsy-hardy).

Nevertheless, the swap partition is there, as seen with "fdisk -l". By the way, my hd setup is: 
       primaries    ntfs(xp), fat32(mydata)
       extended --> ext3(gutsy), ext3(hardy), swap

I found this problem  by hazard, as it didn't lead to any issue, because the system didn't need to swap so far. But it's a potential problem anyway.

Any help would be thankfully appreciated
_________________
TOSHIBA laptop SA50-110  /  Pentium M (0.09) 1596MHz  /  1.1 Cache =64K, 19704 MB/s  /  1.2 cache=2048K, 8674 MB/s  /  Memory=1007Mb 1039Mb/s 
Chipset: Intel i855GM/GME/F SB  99MHz Mobile platform  /  Settings: RAM=165MHz (DDR330) / CAS=2.5-3-3-7

---

### Post by Pumalite on 2008-05-12
Edit etc/fstab and add a line to mount /swap at boot.

---

### Post by JC Cheloven on 2008-05-12
Thanks for your prompt answer :-)
This is my current etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ed568681-153a-4feb-ad80-c4075d76d3ce /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=24e4500c-4577-4d60-8ab3-33cf062a36f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I would say that the required line is already there, isn't it?

---

### Post by Pumalite on 2008-05-12
Check your UUID's with:
blkid

---

### Post by JC Cheloven on 2008-05-12
Ho ho, the blkid command shows this (among others):

> /dev/sda7: TYPE="swap" UUID="d3de1f51-7a24-4f80-97cb-552671126ff2"

This UUID is different from the one in etc/fstab. I can't figure out how this can happen. Anyway, I have to edit fstab to change this UUID, right? And, have I to create some directory in /media as well? (I think I don't, but asking just in case...)

---

### Post by VMC on 2008-05-12
> **JC Cheloven said:**
> Ho ho, the blkid command shows this (among others):



This UUID is different from the one in etc/fstab. I can't figure out how this can happen. Anyway, I have to edit fstab to change this UUID, right? And, have I to create some directory in /media as well? (I think I don't, but asking just in case...)

You maybe resized or reformat your hard drive, perhaps. Yes, try changing fstab to relect what blkid shows. If that doesn't work, you can use either gparted(if installed) to remove and reinstall swap or delete swap and type mkswap /dev/sdax , swapon /dev/sdax

---

