---
title: "Stuck at GRUB Loading"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by LoneWolf3574 on 2005-09-11
I'm running Ubuntu exclusively on one of my computers. Please help, I'm a total newbie with Linux.  It installs just fine, but when I bootup the computer all I get is "GRUB Loading, please wait...".  I'm on my 3rd install  ](*,)  right now after doing a format and resetting the master boot record on the disk using a Win98SE floppy (fdisk /mbr).  Any help would be greatly appreciated.   If it helps any my hardware is as follows:

ABIT KT7A-RAID w/ an AMD K6 @ 1005Mhz
640 Mb of PC-100 Ram
60 Gb WD HDD
Creative 54x CDROM
Sony DVD+/-RW
LinkSys 10/100 Ethernet
ATI Radeon DDR w/ 64Mb
Creative SoundBlaster Live! 5.1 Platnium
Belkin USB 2.0 Card
Logitech Cordless Optical Trackman
Microsoft Natural Keyboard Pro
Belkin USB KVM (for the monitor, switch is powered by a 1.1 USB port)
ViewSonic A90f+

Thanks in advance.

---

### Post by Osamabingandhi on 2006-05-26
this is a really late post. But i have the same motherboard and there seem to be a problem with the disk-raid controller...It writes over the bootsektor or something like that. If you move your bootdisk to the the other controller it  should work fine(there is two of them four harddisks with two green-connectors and two with black-connectors. My ubuntu destroyed my raid set up of two 160gb disks, so be sure to not having any windows on a raid setup when you install...

---

