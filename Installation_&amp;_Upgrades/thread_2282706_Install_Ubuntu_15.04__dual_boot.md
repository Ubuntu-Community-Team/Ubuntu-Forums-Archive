---
title: "Install Ubuntu 15.04  dual boot"
date: 2015-06-16
forum: Installation &amp; Upgrades
---

### Post by sysone on 2015-06-16
My Asus laptop has Win 8.1.
I need to install Ubuntu 15.04 for dual boot.
Looking at the Screenshot , do I just shrink the large partition /sda4  and make 2 new partitions FAT32 for Ubuntu?
I understand that Windows does not make it easy to install Ubuntu - so what should i expect?
Thanks

---

### Post by yancek on 2015-06-16
You should us the windows Disk Management software to shrink the large ntfs partition so that you have the unallocated space you want on which to install Ubuntu.You will see an option during the install to select where to install if you use the manual installation method which is called "Something Else" in Ubuntu.  If your laptop has a preinstalled version of winsdows 8.1, you are likely using UEFI so you will need to select to install Ubuntu UEFI.  You might do an online search for dual-boot with UEFI or wait for someone else to come along.  I don't use it myself so can't give you any specific suggestions.

---

### Post by RobGoss on 2015-06-16
Hello and welcome, If your machine is a newer model them you might want to read these documentations which explains everything you need to do to install a dual boot. [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) . When installing Ubuntu it will give you the option to install Ubuntu along side of Windows if this is what you want. Then just follow the instructions and give that partition as much disk space as you would like then just complete the installation. Good luck

---

### Post by grahammechanical on 2015-06-16
More reading

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It would be very unusual for a pre-installed Windows 8.1 not to be installed in EFI mode so take note of this:

> if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too.

Oh, by the way, Linux has its own file system format. The present default file system is called Ext4. The installer will automatically create 2 partitions, one for Ubuntu (Ext4) and one for swap.

Regards.

---

