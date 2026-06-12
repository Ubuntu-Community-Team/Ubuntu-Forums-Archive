---
title: "Please Help Me With Simple Problem! :'("
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by thelonelywind on 2010-12-11
Hello, and thank you for reading. 

Objective : Boot Ubuntu from partition using NeoGrub and Ubuntu 10.10 ISO files (ISO files are on the partition) 

The other day I made a partition (hd0,2) and used Unetbootin to install the Ubuntu 10.10 ISO to that partition which basically just extracted the ISO to the partition. Then I installed NeoGrub to the Windows Boot Menu and after I choose NeoGrub I insert these commands to try and load/boot Ubuntu like I would from lets say... a usb. 

I type in .... 

root=(hd0,2) (Sets GRUB's root device to the drive where the OS images are stored)

#2 kernel /casper/vmlinuz (Load the kernel image)

#3 module /??????/?????? (Load Module) 

#4 boot


So my problem is, (I HAVE NO IDEA HOW TO LOAD MODULE LIKE I DID KERNEL!) where do I locate the module file in the Ubuntu ISO files that I put on the partition (so that I can load the module and boot)? Or if I'm just doing it plain wrong help me out please! I am rather new to Ubuntu.

---

