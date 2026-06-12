---
title: "Ubuntu 6.10 won't recognize my RAID0"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by lizardman on 2006-11-14
Hi,

first off I have to mention that I'm a total noob with Linux. Today I finally decided to reformat my old Pentium4 and install a small partition with WinXP on it and fill the rest with Ubuntu Linux.

The system has a RAID0 array running, the motherboard is an Asus P4C800-E Deluxe with an Intel 82801ER (ICH5R) SATA RAID Controller.

I've booted with the Live CD and installed dmraid like explained in the RAID HowTo guide ([http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)).
After that, the Raid array will not appear in gParted but it appears in the Installer dialog. However in the installer if I choose to define partitions on the array by myself, it will bring me to a gParted similar interface where I'm not able to choose the Raid array either.

It would be cool to get some help on this as I'm completely lost.

PS: I could use Partition Magic booted from CD to setup Linux partitions but I'm not sure if this helps nor do I know what partitions to define exactly for Linux.

Thanks for any help!

---

### Post by mariuz on 2006-11-14
on board raid is usually not recognized by the kernel or driver is in bad shape 
best advice is to create an pure software raid from ubuntu (only after you backup your partitions)

create an partition for windows on first drive let's call it /dev/sda1
and then create the same size partition /dev/sdb1 on second drive 
after that what is left can be used for software raid (at install time)
the left partition sizes must be the same (/dev/sda2 and /dev/sdb2)

---

