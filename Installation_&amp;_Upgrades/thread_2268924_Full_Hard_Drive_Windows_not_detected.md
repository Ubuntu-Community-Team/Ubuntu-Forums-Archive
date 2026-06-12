---
title: "Full Hard Drive Windows not detected"
date: 2015-03-12
forum: Installation &amp; Upgrades
---

### Post by akshay18 on 2015-03-12
Hi, 
  
 I am new to ubuntu, and doing a dual boot on my Windows 8.1 machine. I went through the instructions on Ubuntu forums to do the same. I was able to successfully boot up using a USB. Next I connected to the internet, and then went ahead with the installation process. During the process, it showed me that it could not detect another OS on the system. However, it does show the hard drive partitions including the EFI, but it shows no free space on the hard drive. I am not able to think of a way to move forward. 

Any help with this issue would be greatly appreciated. Thanks!

Akshay

---

### Post by oldfred on 2015-03-12
Be very careful of this major bug. You really need to use Something Else, have full backups of efi partition and Windows and only use Windows to shrink the NTFS partition. These are all good practices anyway, but now required. I think only the beta version of 15.04 has mostly fixed this bug.
 
Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but mulitiple drive installs must use Something Else. And fix is not in current versions.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

See link in my signature below for lots more info.

---

### Post by grahammechanical on 2015-03-12
Windows 8.1 will be installed in EFI and that means that Ubuntu needs to be installed in EFI mode. Please confirm that you are installing Ubuntu in EFI. What install option did you choose? Install Alongside? Erase disk and Install Ubuntu? Or Something Else? Should there be free space on the drive? 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

