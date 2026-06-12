---
title: "GRUB error 17 &amp; RAID 0"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by steiny on 2007-08-14
Hi,

I have been struggling majorly trying to get Vista and Ubuntu 7.04 to dual boot.

I keep going from one problem onto another and I'm pretty close to giving up. Here is all the info I can think of giving you, how relevant it is I'm not sure.

I have 2 80GB SATA HD's, and a SiS 655FX chipset. My 2 HD's are setup with RAID 0.

I'm currently using the Ubuntu Live CD to boot.

I had Vista installed fine until I tried to install Ubuntu, then neither worked (GRUB error 21).

I formatted my HD's and then neither OS would install, Ubuntu had some GRUB error and Vista froze during the performance test.

I don't know much (anything) about RAID, but during start up I went into the SiS RAID utility and deleted the RAID but did not change how the HD's are connected to the mobo (In BIOS there are no IDE drives except my DVD drive, what this means I don't know).

Then Ubuntu installed perfectly and all was well. I tried to install Vista to a new partition but same problem.
(NOTE: whether the RAID is setup or not Ubuntu still saw the HD's separately, unlike Vista where it sees them as 1 HD, which actually wasn't the case when I first installed it, it was 2 separate HD's)

Then I set the RAID back up and managed to get Vista to install fine, then I installed Ubuntu and I get GRUB error 17.

I then tried putting Super GRUB on USB (again) and this too gives me GRUB error 17.

I thought maybe I need to install the SiS SATA driver for linux, but I have no idea how to do this (I tried following the instructions in the read me included with the driver but I get a couple of errors which I havn't been able to find any help for).

########## FDISK OUTPUT ##########

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7118    57175303+   7  HPFS/NTFS
/dev/sda2            7119        9468    18876375   83  Linux
/dev/sda3            9469        9729     2096482+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 1025 MB, 1025024000 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         124      995998+  83  Linux
ubuntu@ubuntu:~/Desktop/sis_sata_20060508$ 

########## END FDISK OUTPUT ##########



########## MENU.LST ##########

...
default		0
...
timeout		10
...
# hiddenmenu
...

title		Windows Vista
rootnoverify	(hd0,0)
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8b64872f-f2eb-46f9-9de9-ef64ad710bb1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8b64872f-f2eb-46f9-9de9-ef64ad710bb1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

########## END OF MENU.LST ##########


I would really apreciate your help, even if it is just pointing me in the right direction. There is so much junk on the internet now I can't even find any decent RAID help.

---

### Post by steiny on 2007-08-15
Ok, finally some progress. I managed to install Vista. During installation, Vista saw both HD's as one unused space, so I made 2 partitions of equal size. Then I split one of them into a 20GB partition. So I ended up with the following:
Disk 0, Partition 1 = 20GB (unformated)
Disk 0, Partition 2 = 54.5GB (NTFS)
Disk 0, Partition 3 = 74.5GB (NTFS, in the hope that I could uses the guided installation with Ubuntu, so that it would automatically use the 20GB partition)

However Ubuntu cannot see the partitions that I made with the Vista installer. Ubuntu only sees 2 devices; sda and sdb. I ran the installation for Ubuntu and it showed:
/dev/sda
/dev/sdb
       sdb1           NTFS           80GB

Is there anyway I can get Ubuntu to see the partitions like Vista does?

---

