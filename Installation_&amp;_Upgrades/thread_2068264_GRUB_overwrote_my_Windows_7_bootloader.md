---
title: "GRUB overwrote my Windows 7 bootloader"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by bscott433 on 2012-10-08
I did an install of Ubuntu 10.04 to an external USB drive which was successful. I chose the option to write GRUB to this external drive thinking it would not affect my Windows 7 boot drive.
It did, when I try to boot I get a GRUB error:
GRUB loading.
error: no such disk
grub rescue)_

Any ideas how to fix the Windows startup disk? I'm not planning to use the USB drive on this PC but send it to a friend who would like to use the USB drive to boot and run Ubuntu on his laptop,

TIA,
Brian

---

### Post by oldfred on 2012-10-08
The easiest way is to install and run Boot-Repair to your liveCD or USB. It will direct you to to reinstall grub2's boot loader to the external and install a Windows like boot loader to your internal drive.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

You can directly install grub2's boot loader to the USB, if you can boot your Ubuntu from liveCD.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

