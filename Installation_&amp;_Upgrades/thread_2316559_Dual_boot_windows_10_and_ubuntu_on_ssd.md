---
title: "Dual boot windows 10 and ubuntu on ssd"
date: 2016-03-09
forum: Installation &amp; Upgrades
---

### Post by Krum_Manasiev on 2016-03-09
Hello, I would like to ask the following: I bought a laptop with pre-installed windows 10. The laptop has 256 SSD hard drive. For the purpose of dual boot I shrunk the drive and now it has the following partitions: Windows 10 / Un-allocated space of 60 Gb (Ubuntu part) / Un-allocated space of 2 Gb (swap) / and the remaining for storage purpose. The un-allocated space will be formated during Ubuntu installation. Is this configuration OK for the dual OS? What am interested, at the end when everything is done with installing, will I get the grub screen with the option to select OS? Excuse my question if it is not well formed. I am not familiar with the latest SSD, UEFI and so on particularities. Thanks

---

### Post by yancek on 2016-03-09
Read the Ubuntu documentation at the link below on dual-booting using UEFI before beginning.  If windows 10 was pre-installed, it is almost surely UEFI mode.  You can check to see if you have a small FAT32 partition near the beginning of the drive. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Are you familiar with Linux device/partition naming conventions?  If not, do some research as it is totally different than windows.  If you have only the one drive, it shouldn't be much of a problem.  As explained in the link above, if you have windows UEFI then you must also install Ubuntu UEFI or one of the systems will not boot.  I would suggest you select the "Something Else" to install and read the documentation at the link above carefully before beginning.

---

