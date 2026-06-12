---
title: "LiveCD to hard drive"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by Databit on 2008-11-25
How would I go about putting the LiveCD/installer on my spare partition /dev/sda6?
I tried 
dd if=ubuntu-8.10-desktop-i386.iso of=/dev/sda6
with the partition formatted as fat16 and fat32 each time the system just marks it as unknown partition type after doing the dd. I'm trying to make this like a recovery partition that I can go reinstall ubuntu from or just boot to the livecd but hd based

---

### Post by logos34 on 2008-11-25
[here ]("https://help.ubuntu.com/community/Installation/FromLinux")you go

---

### Post by Databit on 2008-11-25
> **logos34 said:**
> [here ]("https://help.ubuntu.com/community/Installation/FromLinux")you go
Very close to working like a champ.
Got it on the partition looks like my problem was I was doing FAT instead of ext3

problem now is that when I boot from in the installer doesn't see the rest of the disk. including the 153 gigs of unallocated space

gparted and fdisk can see it just not the installer. any ideas?

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc53ba248

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2       300431565   312576704     6072570    5  Extended
/dev/sda5       300431628   307596554     3582463+  82  Linux swap / Solaris
/dev/sda6       307596618   312576704     2490043+  83  Linux

---

