---
title: "Grub, RAID and software mirror C:"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by LiLoather on 2008-07-18
I'm considering installing Kubuntu to the last 40GB of an 80GB IDE drive in my system.  Please help with the following:

1.  The first partition of this drive (hdc) contains a software mirror of my Windows XP drive C: on hda.  On booting, Windows offers me a choice of booting either, presumably from bootini.  Will this be effectively incorporated into GRUB?  

2.  Can Grub cope with booting Ubuntu from beyond 30GB into a disk?

3.  I have a FAT32 partition on a hardware RAID 0 array which is dedicated to a Windows Swap/Page file.  Is it possible to get Linux to use the same partition for its Swap, presumably utilising FAT32 format?

---

### Post by logos34 on 2008-07-19
> **LiLoather said:**
> 
2.  Can Grub cope with booting Ubuntu from beyond 30GB into a disk?


Yes, if your Bios can.  If not (as is the case with older Bioses), you can always create a separate /boot at the front of the disk.

---

