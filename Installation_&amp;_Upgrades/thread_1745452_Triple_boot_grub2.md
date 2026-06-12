---
title: "Triple boot grub2"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by John_Rose1 on 2011-05-01
Hi, I am not a programmer and would appreciate help on a complex problem:

I now have Ubuntu (10.4) and Windows 7 booting fine with Grub2 in MBR on my Dell Vostro notebook.

The partitions are as follows:
1. MBR
2. Windows 7 recovery (boot flag set)
3. Windows 7 Professional
4. Extended partition with NTFS data and then Ubuntu

My problem is that I need XP, and I don't need Windows 7 but would prefer now not to erase the latter (note that XP mode under Windows 7 is horrible - not a good solution).

I don't need the recovery partition since I have a recovery CD-ROM and would like to install XP in primary partition 2 and then get a triple boot from Grub2 to XP, Windows 7 and Ubuntu (or a double boot XP and Ubuntu with possibility of later activating Windows 7). I can't easily understand which partitions Grub2 will find without playing with scripts (I guess only the one with the boot flag plus Ubuntu?).

What I propose to do (if it will work) is:
1. Reformat partition 2 and install XP there (I guess that will set the boot flag for that partition)
2. Upgrade Ubuntu to 11.04

Hopefully I will then get a double boot Ubuntu-XP. My question is then, if my XP does not work as I want, would I able to set boot flag on the Windows 7 partition (direct booting, not through erased recovery partition) to automatically get Ubuntu-Windows 7 double boot (or do so by reinstalling Grub2)? I would not want to be in situation where my existing Windows 7 is unusable, since I guess if I have to use the recovery CD-ROM  I would have to save all of my data and redo my partitions to get the double boot back.

Waiting for your advice before I plunge, thanks, John

---

