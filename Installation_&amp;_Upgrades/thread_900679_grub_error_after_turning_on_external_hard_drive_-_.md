---
title: "grub error after turning on external hard drive - error 21"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by wattz3 on 2008-08-25
Hi,

I'm having a problem with GRUB when I turn on my external hard drive. I've had ubuntu running smoothly for a few days, but I noticed when I have my external (SATA) hard drive turned on when I boot my computer I'm getting an error in GRUB. The error code is 21.

Why is this happening and how do I fix grub to work whether my external drive is on or off?


FYI, I have a dual boot with windows xp on another drive.

---

### Post by Pumalite on 2008-08-25
Check this thread:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by wattz3 on 2008-08-25
Hi,

Thanks for the reply. But I don't see anything helpful for me from that thread. I'm not trying to install ubuntu or anything else on the external drive... I just turn it on. Nothing else... and then grub fails when i boot.

---

### Post by Pumalite on 2008-08-25
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by gatenby_jp on 2008-08-25
Your problem relates to how your bios reports the hard disks ... I first ran into error 21 when I added an ide drive to a server than had run out of sata slots ... the bios then reported the hda as disk0 and the satas as disk1, disk2. Grub makes use of this order from the bios. If your bios allows you to set the order of the hard disks you can ensure that the usb drive does not suddenly become the first drive ... The secret of a dual boot is to have both grub and / on the same hard disk as the booting mbr. You only need say 2gigs for this purpose on the other hard disks you then have 3 mount points or partitions /usr, /var, /home. 

Once the booting process starts loading the /etc/fstab ... the uuid's of the partitions are used and those dont change regardless of how the bios reports the disk order. 

If you do sudo fdisk -l with the external disk turned off and then again with it turned on and recognised by the system and compare the results you will probably see that the usb disk comes first in the order reported. This will definitely be the case if the bios supports booting from a usb drive ... if you can turn this feature off in the bios it may solve the problem.

The grub experts might have a solution ...

I first ran into the problem on a server where i added a an ide hard disk ... my sata slots were full ... luckily i could edit my grub menu.lst as the change was permanent in your case it is dependent on whether you have the disk plugged in or not ... this is also a problem to Windows where the USB drive is set as bootable ...

---

### Post by wattz3 on 2008-08-25
hi gatenby,

i've been trying to manually modify my menu.lst and device.map files with no success...

the problem is fixed (well temporarily) by re-installing grub when my external hard drive is turned on. 
But now, when I turn off my external hard drive I get the same error...

I guess GRUB wasn't meant to be used in such a way where the drive mappings continue to change. And unfortunately I can't set hard drive order in the bios...

---

### Post by Pumalite on 2008-08-25
Edit menu.lst of your USB and change 'groot' and 'root' to (hd0,0)

---

### Post by caljohnsmith on 2008-08-25
> **wattz3 said:**
> Hi,

I'm having a problem with GRUB when I turn on my external hard drive. I've had ubuntu running smoothly for a few days, but I noticed when I have my external (SATA) hard drive turned on when I boot my computer I'm getting an error in GRUB. The error code is 21.

Why is this happening and how do I fix grub to work whether my external drive is on or off?

So when your SATA HDD is not connected, you are able to use Grub OK to boot Ubuntu, but when you connect the SATA HDD, you never get a Grub menu on startup and instead get an error 21? If that is true, it sounds like your BIOS might be set to boot the SATA HDD, but when you disconnect the SATA HDD, BIOS defaults to booting your internal HDD. 

What is on the SATA HDD? You say:
> **wattz3 said:**
> FYI, I have a dual boot with windows xp on another drive.
What is this other HDD you refer to?

---

### Post by wattz3 on 2008-08-25
> **caljohnsmith said:**
> So when your SATA HDD is not connected, you are able to use Grub OK to boot Ubuntu, but when you connect the SATA HDD, you never get a Grub menu on startup and instead get an error 21? If that is true, it sounds like your BIOS might be set to boot the SATA HDD, but when you disconnect the SATA HDD, BIOS defaults to booting your internal HDD. 


That's exactly right. The grub menu never appears, and I get error 21. **But this also happens when I disconnect another hard drive (that doesn't contain my MBR).**

> **caljohnsmith said:**
> 
What is on the SATA HDD? 

My main drive (with mbr) is one of my SATA HDD's. The 2nd SATA HDD is my 'external' drive that i'm turning on and off... there's only backup files on it.

> **caljohnsmith said:**
> 
What is this other HDD you refer to?

I have 5 'internal' hard drives listed below (sdd has 2 partitions).

/dev/sda1 - MBR, windows xp
/dev/sdb1 - files
/dev/sdc1 - files
/dev/sdd1 - files
 /dev/sdd2 - ubuntu
/dev/sde1 - files

**So even when I disconnect one of my other HDDs that only have files (leaving windows and ubuntu) I still get the grub error 21.**

---

### Post by caljohnsmith on 2008-08-25
OK, to get a clearer picture of your setup, please post the output of the following commands:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)
grub> geometry (hd3)
grub> geometry (hd4)
```

---

### Post by wattz3 on 2008-08-25
> **caljohnsmith said:**
> OK, to get a clearer picture of your setup, please post the output of the following commands:
sudo fdisk -lu


this is with my 2nd SATA drive (external) turned off, and also with sde disconnected since it's now dead :(



```
root@wanker:/# fdisk -lu

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfad4fad4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    72292499    36146218+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa9c8a679

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   390716864   195358401    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd259f1b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   490223474   245111706    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ddea759

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   914194889   457097413+   7  HPFS/NTFS
/dev/sdd2       914194890   976768064    31286587+  83  Linux

```

> **caljohnsmith said:**
> 
sudo grub
grub> find /boot/grub/stage1

```
grub> find /boot/grub/stage1
 (hd3,1)

```

> **caljohnsmith said:**
> 
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)
grub> geometry (hd3)
grub> geometry (hd4)

```
grub> geometry (hd0)
drive 0x80: C/H/S = 4500/255/63, The number of sectors = 72303840, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd1)
drive 0x81: C/H/S = 24321/255/63, The number of sectors = 390721968, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd2)
drive 0x82: C/H/S = 30515/255/63, The number of sectors = 490234752, /dev/sdc
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd3)
drive 0x83: C/H/S = 60801/255/63, The number of sectors = 976773168, /dev/sdd
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83

```

---

### Post by caljohnsmith on 2008-08-25
I think I know what is going on:
[LIST]
[*]Your Ubuntu partition is sdd2, or (hd3,1) as Grub found it.
[*]Grub is in the MBR of sda, *but it points to sdd2 or (hd3,1) for its configuration files* (menu.lst, stage2, etc)
[*]The problem I think is that when you connect/disconnect that other HDD, then the Ubuntu HDD is no longer the 4th HDD or sdd, but something else (maybe sdc or sde). And since Grub always looks on the 4th HDD for its files, it doesn't find them when you change things around.
[/LIST]
Probably the most ideal solution to your problem would be to install Grub to the MBR of your Ubuntu HDD, and then set the Ubuntu HDD to always be the first to boot in BIOS. But if for some reason you can't do that, you have at least two other alternatives:
[LIST]
[*]Install GRUB4DOS on your sda Windows HDD, and that will keep everything Grub related on sda, independent of all other HDDs.
[*]Make a super dinky 10 MB dedicated Grub partition on sda. Like the GRUB4DOS method, this makes it so Grub is entirely independent of all your other HDDs.
[/LIST]
I've used both methods above with success, so I know they work.

---

### Post by wattz3 on 2008-08-25
> **caljohnsmith said:**
> I think I know what is going on:
[LIST]
[*]Your Ubuntu partition is sdd2, or (hd3,1) as Grub found it.
[*]Grub is in the MBR of sda, *but it points to sdd2 or (hd3,1) for its configuration files* (menu.lst, stage2, etc)
[*]The problem I think is that when you connect/disconnect that other HDD, then the Ubuntu HDD is no longer the 4th HDD or sdd, but something else (maybe sdc or sde). And since Grub always looks on the 4th HDD for its files, it doesn't find them when you change things around.
[/LIST]
Probably the most ideal solution to your problem would be to install Grub to the MBR of your Ubuntu HDD, and then set the Ubuntu HDD to always be the first to boot in BIOS. But if for some reason you can't do that, you have at least two other alternatives:
[LIST]
[*]Install GRUB4DOS on your sda Windows HDD, and that will keep everything Grub related on sda, independent of all other HDDs.
[*]Make a super dinky 10 MB dedicated Grub partition on sda. Like the GRUB4DOS method, this makes it so Grub is entirely independent of all your other HDDs.
[/LIST]
I've used both methods above with success, so I know they work.

Thanks for the help. I'll give that a try!

---

### Post by gatenby_jp on 2008-08-26
This would be my workaround:

Take your sata 1 Drive and move all the data onto one of the other drives that have files ... you can best do that by mapping "My Documents" in XP to a different drive. now creat a partition on that drive big enough for the Ubuntu install say 12 Gigs however during install choose manual partitioning and install with that drive as the mount point for /    then include your existing linux drive as the mount point for /home ... you could also create mappings for all the other disks ... eg a mount point /external fs ntfs ... do not format. The install will create a /etc/fstab with uuid identifiers and not simply /dev/sda ... etc 
Now as long as the disk with mbr , windows and linux is always the first drive ... grub will not come unstuck ... then as /etc/fstab is mounting drives by uuids ... it should always find the correct drives.

---

### Post by caljohnsmith on 2008-08-26
> **wattz3 said:**
> Thanks for the help. I'll give that a try!
Let me know if you want any more details about the particulars of actually implementing any of the scenarios I suggested. And even if you don't need further assistance, it would be great if you could post back whatever solution you come up with so others who search the forums will benefit too. :)

---

