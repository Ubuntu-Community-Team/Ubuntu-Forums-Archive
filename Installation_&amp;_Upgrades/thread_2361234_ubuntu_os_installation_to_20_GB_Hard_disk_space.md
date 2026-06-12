---
title: "ubuntu os installation to 20 GB Hard disk space"
date: 2017-05-14
forum: Installation &amp; Upgrades
---

### Post by elururajesh on 2017-05-14
Hi

I have 80GB hard disk with 4 partitions (20,20,20,20), Now I would like to install in one 20Gb space ubuntu os

System specification:
pentium processor 2.66GHz
ram 1.5 Gb

can any one suggest me some version to install ubuntu os in my system

Thanks,
RajeshBabu

---

### Post by RobGoss on 2017-05-14
Hello and welcome, With only** 1.5 GB **of Ram I would recommend using a light weight distribution like Lubuntu. Are you trying to dual boot your system?

If you are I would also recommend you do your homework before you attempt to run a dual boot system, making a complete backup of your system is a good approach just in case something goes wrong. This might be a good place to start please see the following documentation, [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by elururajesh on 2017-05-14
I am not trying to dual boot, only ubuntu 
If I install Lubuntu in my pc(20GB), shall I access(from Lubuntu) the contents of remaining 3 partitions data(20GB each)

---

### Post by RobGoss on 2017-05-14
If you boot in to Lubuntu or what ever OS you choose to use as long and the data partition is mounted you should be able to see that partition listed. You might have to use **disks tool **to get that partition mounted, once that's done you should be able to access what data partition you need to retrieve

This is only to show you how things may look once it's mounted, this is accessing partitions from Windows and it should not be much of a difference but I'm sure it can be accomplished  [http://linuxbsdos.com/2012/01/02/how-to-access-microsoft-windows-files-and-folders-from-linux/](http://linuxbsdos.com/2012/01/02/how-to-access-microsoft-windows-files-and-folders-from-linux/)

---

### Post by oldfred on 2017-05-14
Some of the auto install options erase entire drive.
With existing partitions best to only use Something Else install option.
Choose (change) partition you want for install, make ext4 format and / (root). With only 1.5GB of RAM you should also have about 1.5GB of swap.

       Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

Since you may have used all 4 primary partitions allowed with MBR(msdos) partitioning, you can erase 20GB, convert to extended partition and then add two logical partitions. Ubuntu works fine from logical partitions. Only Windows requires a primary partition to boot from.
       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

### Post by Impavidus on 2017-05-14
As indicated above, you can install Lubuntu in one of your 20GB partitions and you'll be able to access files on the other partitions. Before 17.04 Ubuntu also uses a swap partition, so the installer will have to create one. From 17.04 on the default is a swap file. It doesn't matter much.

You suggest that your 4 partitions already exist and you want to use them. If you don't already have Linux on that computer, I doubt those partitions are Linux partitions, although you didn't say. Linux can read and write Windows partitions, but cannot fix them if damaged, so if you run Linux only on this computer, best make all partitions Linux partitions.

---

