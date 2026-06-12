---
title: "Grub - Error 17 Message"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by TheReconHunter on 2006-09-26
Hey. I just installed windows on another computer of mine, to dual boot with ubuntu. After the install, I used the Live-cd to restore grub. However, when i try to select ubuntu as the OS i want to log into, i get the message Error 17: cannot mount partition? Now im totally stuck ](*,) and I cannot use Ubuntu. Any ideas as to wehre to go next? Thanks.

** edit- here is my sudo fdisk -lu


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6994    56179273+   7  HPFS/NTFS
/dev/hda2            6995       23408   131845455    5  Extended
/dev/hda3           23409       24172     6136830   83  Linux
/dev/hda4           24173       24321     1196842+  82  Linux swap / Solaris
/dev/hda5            6995       23408   131845423+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo fdisk -lu

---

