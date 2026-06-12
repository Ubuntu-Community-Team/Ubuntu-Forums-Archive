---
title: "Installing Breezy on a dual boot system with EZ-bios"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by egas77 on 2005-11-26
Greets all,

I'm trying to get Ubuntu 5.10 installed on a friend's computer, which currently dual boots RedHat9 and Windows 2000.  We are trying to replace RedHat 9 with Breezy.

He used EZ-bios to set up the harddisks, creating several partitions on the master and slave. While the existing RedHat and Windows see all the partitions just fine, during installation  the Ubuntu partition manager sees only the one partition on each.

Switching over to the F2 screen and running fdisk to display the partition table of each disk shows only one partition, with an ID as 55 and System as EZ-Drive.

He claims he didn't have to do anything special with RedHat or Windows to get them to install, and would like to keep the existing Windows partions (he made several). Is there any way to get Ubuntu to recognize these and install correctly?

Thanks much.

---

### Post by rmicroys on 2006-02-04
I'm having a sort of similar problem.  I'm in the process of rebuilding all the OS's on one of my machines and taking this opportunity to put Linux on for the first time.  I'm a total newb here.  My computer is a PII-400 with a 8GB main drive split in half.  One for the W2K OS, and one for Ubuntu.  I have EZ-bios for my 40GB (FAT30) drive.  The grub boot loader has seemed to clobber over EZ-bios code on the primary drive's partition and I can't get Windows to see the 40GB drive anymore.  Trying to re-install the EZ-bios code doesn't seem to do much either.  Linux can use the 40GB drive just fine.  Any suggestions on how to get this computer setup - without buying a seperate HDD controller for the drive?  Thanks.  At least it hasn't killed my primary drive - it at least still boots.  Now just winderz is pretty useless on a 4gb partition (not that it really ever was that useful in the first place!)

---

