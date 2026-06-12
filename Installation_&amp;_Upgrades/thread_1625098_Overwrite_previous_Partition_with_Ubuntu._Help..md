---
title: "Overwrite previous Partition with Ubuntu. Help."
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by ssoRRoss on 2010-11-18
Hello, Sorry if this is in the wrong place. I am completely new to Ubuntu forums, and Ubuntu itself.
I currently dual boot Windows 7 and Ubuntu, but I have somehow broke Ubuntu and would like to, if possible (which im sure it is) reinstall the newer one with a cd.
The shortened version is, when I'm installing it, I have to select the place it goes. Problem: I dont know which (partition?) to overwrite. 
I asked on Yahoo Answers and was told to enter sudo fdisk -l
I got the following:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12288000   27  Unknown
/dev/sda2            1530        1543      102400    7  HPFS/NTFS
/dev/sda3            1543       18289   134512462    7  HPFS/NTFS
/dev/sda4           18290       30401    97289640    5  Extended
/dev/sda5           18290       29903    93289423+  83  Linux
/dev/sda6           29904       30401     4000153+  82  Linux swap / Solaris

Problem 2: I have no idea what to do with this information. If i want to overwrite the old Ubuntu which option to I select? Please explain this in beginners terms as I am very new. *Also, if you can tell from that information, which part is the Windows?*The person on Yahoo said something about a swap partition and I dont even know what that means. :confused: Please help me, as I really want to use Ubuntu again. Sorry, and Thank you :)

---

### Post by zvacet on 2010-11-18
From your output Ubuntu is on sda5,so that is partition you want to delete and install new Ubuntu there.Just choose format ext4 and mark it as root / .You will see options when you come to partition stage.

---

### Post by drs305 on 2010-11-18
Just select manual partitioning during the installation. You don't really even have to *delete* the partition, just select sda5 as the partition on which to install Ubuntu. Make sure to tick the "format" box and choose "/" as the mountpoint. Ubuntu will find your existing swap partition and use it automatically.

---

