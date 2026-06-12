---
title: "Kernel panic when booting ubuntu 14.04"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by octohedra on 2014-10-20
Well hello friends ):P

A couple of days ago i was working on ubuntu as usual and the comptuer started crashing with I/O errors, so i decided to check my hard drive and found it could be damaged, showing up to 340 bad sectors or blocks.

So i backed up my crucial data and proceeded to install ubuntu again, hoping the errors would magically disappear on my sda3 partition, just like before, so i merged my sda3 partition with two others that were after it and proceeded to install it, hoping to get two birds stoned at once :roll:

Ubuntu installed normally and then when i tried to access it for the first time, i couldn't, this is all i get

[IMG]http://i.imgur.com/EVb3BZd.jpg[/IMG]

Windows, which is in the same hard drive, in sda2, works perfectly.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x637ca5d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000    7  HPFS/NTFS/exFAT
/dev/sda2   *     3074048  1167904767   582415360    7  HPFS/NTFS/exFAT
/dev/sda3      1167904768  1238264142    35179687+  83  Linux
/dev/sda4      1238265854  1250263039     5998593    5  Extended
/dev/sda5      1238265856  1250263039     5998592   82  Linux swap / Solaris

I already tried boot-repair with recommended repair without luck, and also tried some advanced options like "Reinstall GRUB", "Purge GRUB before reinstalling" - *which didn't work at all btw, got a bunch of errors and couldn't purge it* - and "Upgrade GRUB to its most recent version", then recommended repair again.. and notihng.

I really need to get ubuntu running so i can get back to work, i can't stand working on windows, I only use it to edit images.

---

### Post by octohedra on 2014-10-20
Okay i just fixed it. All i have to do was to [B][URL="http://ubuntuforums.org/showthread.php?t=1769102"]follow the instructions on this post. 
[/URL][/B]

---

