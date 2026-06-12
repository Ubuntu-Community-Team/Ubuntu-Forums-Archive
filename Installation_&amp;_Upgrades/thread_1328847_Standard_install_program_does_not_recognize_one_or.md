---
title: "Standard install program does not recognize one or more of my hard drives"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by mbubbles on 2009-11-16
I am trying to install Ubuntu 9.10 using the standard installation live CD
 I have four 320GB SATA hard drives.  On one of these disks I have two Windows XP partitions that use approximately 100GB.  The live cd's the partition manager only recognizes 3 of the 4 drives.  The drive with the widows partition is the missing disk.  However if I open a terminal and run
 sudo fdisk -l. I get:
 

 ubuntu@ubuntu:~$ sudo fdisk -l
 

 Disk /dev/sda: 320.1 GB, 320072933376 bytes
 255 heads, 63 sectors/track, 38913 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0x88088808
 

    Device Boot      Start         End      Blocks   Id  System
 /dev/sda1   *           1        2646    21253963+   7  HPFS/NTFS
 /dev/sda2            2647       38912   291306645    f  W95 Ext'd (LBA)
 /dev/sda5            2647       12200    76742473+   7  HPFS/NTFS
 

 Disk /dev/sdc: 320.1 GB, 320072933376 bytes
 255 heads, 63 sectors/track, 38913 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0x88408840
 

    Device Boot      Start         End      Blocks   Id  System
 

 Disk /dev/sdd: 320.1 GB, 320072933376 bytes
 255 heads, 63 sectors/track, 38913 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0x88408842
 

    Device Boot      Start         End      Blocks   Id  System
 

 Disk /dev/sdb: 320.1 GB, 320072933376 bytes
 255 heads, 63 sectors/track, 38913 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0x88408841
 

    Device Boot      Start         End      Blocks   Id  System
 

 The alternate Live CD does recognize all four hard drives during install.  So I could always just use that or I could install Ubuntu using the standard cd on any combination of /dev/sd[bcd] and then if necessary mount /dev/sda, edit the fstab and a have a functional system.  The problem that I am having is that my primary goal in installing Ubuntu is to learn something.  And I can't seem find a way to explain and fix the problem of not all drives being recognized during a standard install.   
 

 One theory that I had was that because at various times I have had RAID arrays set up on these disks (both linux RAID (mdadm) and fakeRAID) maybe somewhere remnants of that existed on one or more of the disks.  Further supporting this theory is that when I run the alternate install disk I am presented with the question:
 

 "One or more drives containing Serial ATA RAID configurations have been found do you wish to activate these RAID devices?"   
 

 I have verified that the BIOS settings on my ASUS EP45-UD3P mother board have the RAID controller disabled and I have no linux raid partitions on any of the disks so I really don't understand why RAID devices are detected.
 

 It occurred to me that maybe RAID data was stored on a part of the disk which was not altered during a standard format so I tried to delete any data on the disks which may have persisted through multiple formats by using the dd if =/dev/zero of =/dev/sda bs=1M command and then reformatting.  This did not change anything.
 

 I tried to use the standard installation live cd for version 8.04 to see what would happen and found that none of my hard disks were recognized either by the installer program or by fdisk.  From what I understand the standard installer on version 8.04 does not have mdadm or dmraid so again I suspect a problem with me not properly resetting my hard drives after they were in a RAID array.
 

 Thus far I haven't been able to understand why all of my hard drives are not being recognized by these standard installation cds.  In trying to do so I have run around in a lot of circles, which has been educational but not successful.  How can I determine definitively if one or more of my hard drives are being identified as RAID devices?  If it is a RAID problem how can I remove all RAID information from these disks and if it isn't what other theories should I explore?

---

### Post by 3vi1 on 2010-01-09
I had the same issue with my *Gigabyte* EP45-UD3P (I assume you mispoke when you said it was an Asus board).

I too had previously had RAID arrays defined and found that only the alternate install CD allowed you to ignore these now non-raid devices.  Apparently the BIOS isn't cleaning something off the drive when you delete the raid array?

I'm not at all impressed with the FakeRAID on this board:  The array breaks for seemingly little reason (booting from an install CD without writing anything will do it), and I'll be damned if I can figure out how to get dmraid to rebuild the broken array (the BIOS seems to suddenly think one of the drives isn't a member of the RAID1 set - so there's no spare to rebuild).

Anyway:  Thank you very much for sharing the info.  It's comforting to know that it's not a defect in my individual system.

---

### Post by tachuela on 2010-01-09
It's common. Try disconnecting the "offending" HH

---

