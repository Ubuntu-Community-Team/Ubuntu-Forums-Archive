---
title: "Beginner Please Help"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by carmen0771 on 2008-03-07
Hello,

Please excuse my English first. I need some advice in installing Ubuntu 7.10

I just received two DVD’s Ubuntu 7.10 for Pc and the second with the 64-bit version.

The first installation destroys my windows partitions and is finished with a grub error.

Well I just build this system:

Motherboard Asus P5K3 Deluxe Wifi
CPU Intel Core Duo E 6820 (3000 Hz)
2 GB RAM DDR3 Corsair
VGA Asus EN8600 GT 512 Mb DDR3
2 HD Samsung 500 Gb
2 HD Hitachi 160 Gb ( for Backup)
1 Plextor PX 810 SA
1 Optiarc AD 71735
Case Coolmaster Nvidia Stacker 830
The  4 HD and the 2 DVD-RW are SATA and connected in BIOS as SATA AHCI.
So I have 6 SATA devices SATA AHCI.

I want to have on this PC: Windows XP Pro, Windows Vista and Ubuntu.

I like to have an advice regarding how to make the partitions to install all these OS.
Which will be the order of installation?  ( I suppose Ubuntu to be the last)
How many partitions to make and how many MB. ( NTFS, FAT32?)
Which Ubuntu? 64 bits or 32? The cpu is a 64 bits.

Normally I started with XP then installed Vista and then Ubuntu but I fall in troubles.

Please help me with some advices.

Thanks

---

### Post by jan quark on 2008-03-08
check out this site:

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

and ask whatever is not answered for you
> Which will be the order of installation? ( I suppose Ubuntu to be the last)
How many partitions to make and how many MB. ( NTFS, FAT32?)
Which Ubuntu? 64 bits or 32? The cpu is a 64 bits.

yes I would install ubuntu as the last one
for partitions info you can see this site
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

64 bit is of course the faster choice. but not every driver is supported for the 64 bit architecture.

---

### Post by ssj3strife on 2008-03-08
I imagine this is a pretty common scenario. I did a google search for "ubuntu vista xp triple boot" and it came up with quite a few pages describing the process. Good luck!

---

### Post by prshah on 2008-03-08
Install XP first, on the first drive. When installing, create just a single partiion of about 20Gb for it. Make sure your partition is set to active (XP should do this for you with a fresh drive, if it doesn't boot with a linux/xp live CD and set partition as active using either fdisk). While you are in XP, grab the EXT3 IFS driver: Google for the location.

Next bootup with Vista. Press Shift-F10 during startup, and when at the command prompt, use the command DISKPART to create a new NTFS 30 Gb partition on "Disk0:Unallocated space". Then continue with the install. If asked, choose "no" for upgrade. If asked about upgrade license violations, choose "Retail" or "OEM" or whatever you have, don't choose "Upgrade". Create a new partition for Vista (30Gb is OK or whatever you want). Also install the ext2/3 ifs driver in Vista too. Check your boot manager entries if required.

Finally, boot with Ubuntu live CD. Create a 10Gb partition linux/ext3 on your primary hdd, with mount point "/". Then create another linux/ext3 partition on your secondary hdd (using full space), with mount point "/home". The create a small (2Gb or less) partition on a THIRD drive (160Gb) with type as linux/swap. Install away.

Once all your operating systems are installed, boot into Ubuntu and create ext3 partitions on all unallocated hard disk areas by using Gparted.

Remember EXT2/3 partitions are fully accessible in both Windows XP and Vista once you have installed the EXT2/3 IFS drivers.

Cheers,
PRShah

---

