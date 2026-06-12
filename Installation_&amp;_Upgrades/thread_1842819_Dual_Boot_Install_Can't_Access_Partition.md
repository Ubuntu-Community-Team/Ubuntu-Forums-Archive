---
title: "Dual Boot Install Can't Access Partition"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by IrrationalIntellect on 2011-09-12
It's been like 10 years since I've tried to do this. So I followed the instructions and made a partition on a new Compaq Presario laptop to make room for Ubuntu. When I tried to run the Live CD it said it couldn't access the partition I made.
 
I have since found out that Windows 7 says it can't access the partition either -- even tho' it gives it a drive name.
 
Any ideas where to go from here?

---

### Post by Hakunka-Matata on 2011-09-12
Welcome to the forums;

Can you use Ubuntu from LiveCD, not installing it, but choosing "try without installing"?
If so, please post the output of ```
sudo sfdisk -luS
```
If you can only run from windows, then post a picture of your Disk Manager partition window

---

### Post by IrrationalIntellect on 2011-09-12
```
 
ubuntu@ubuntu:~$ sudo sfdisk -luS
 
Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0
 
Device Boot Start End #sectors Id System
/dev/sda1 * 2048 409599 407552 7 HPFS/NTFS
/dev/sda2 409600 348375039 347965440 7 HPFS/NTFS
/dev/sda3 459524096 488183807 28659712 7 HPFS/NTFS
/dev/sda4 488183808 488395119 211312 c W95 FAT32 (LBA)
 
Disk /dev/sdb: 983 cylinders, 16 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0
 
Device Boot Start End #sectors Id System
/dev/sdb1 237 990863 990627 6 FAT16
/dev/sdb2 0 - 0 0 Empty
/dev/sdb3 0 - 0 0 Empty
/dev/sdb4 0 - 0 0 Empty

```&#12288;

---

### Post by Hakunka-Matata on 2011-09-12
> **IrrationalIntellect said:**
> ```
 
ubuntu@ubuntu:~$ sudo sfdisk -luS
 
Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0
 
Device Boot Start End #sectors Id System
/dev/sda1 * 2048 409599 407552 7 HPFS/NTFS
/dev/sda2 409600 348375039 347965440 7 HPFS/NTFS
/dev/sda3 459524096 488183807 28659712 7 HPFS/NTFS
/dev/sda4 488183808 488395119 211312 c W95 FAT32 (LBA)
 
Disk /dev/sdb: 983 cylinders, 16 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0
 
Device Boot Start End #sectors Id System
/dev/sdb1 237 990863 990627 6 FAT16
/dev/sdb2 0 - 0 0 Empty
/dev/sdb3 0 - 0 0 Empty
/dev/sdb4 0 - 0 0 Empty

```&#12288;

If you are wanting to install ubuntu to sdb, then you're almost there.

should I remind you about making backups of your windows system?

BTW, what is your second drive?, an 8GB SSD maybe:  what size disk is it?  I don't believe the sfdisk output, please tell me what size gparted shows it as.

You want to create some partitions on your second drive, sdb:
open gparted with mouse or type:

```
sudo gparted
```select sdb, upper right hand side selection window:
once you're SURE you're working on sdb, and not sda,
[LIST]
[*]delete sdb1 - it's a FAT partition you do not need it.
[*]create sdb1 - primary, ntfs, (both windows and ubutnu can see this partition, used as a share) size?, how big is your disc?
[*]create sdb2 as a primary, EXtended partition size = all of unallocated left.
[*]create sdb5 as an EXT4, Logical partition, mounted to / (root) size= 15GB
[*]create sdb6 as an EXT4, Logical partition, mounted to /home  size = big
[*]create sdb7 as a swap of size ~=4GB
[/LIST]

after that run the ubuntu installer liveCD and choose sdb5 as the destination for your new install.
Also, when asked for destination of Bootloader (Grub), choose **sdb**
in BIOS when rebooting, choose sdb and as the first disc to boot from, in boot order

---

### Post by IrrationalIntellect on 2011-09-12
Could sdb be the memory stick I was using to copy the terminal?
 
I was dealing with the main hard drive (I assume sda) and unallocated 53Gb for Linux. My plan was for 3Gb for swap, 15Gb for root and the rest for home.
 
Windows 7 showed c:/ as the biggest partition, the restore partition and then the other partition that couldn't be accessed (which I assumed was the unallocated partition I made.)
 
I don't think there are two hard drives.

---

### Post by Hakunka-Matata on 2011-09-12
yes, one minute 
it certainly does look like your 8GB flashdrive, (dooh)

---

### Post by Hakunka-Matata on 2011-09-12
I don't see any unallocated space listed on sda, please post the output of ```
sudo sfdisk -luB
```

That'll show the disc details in MiB.

---

### Post by IrrationalIntellect on 2011-09-12
I increased the unallocated by 15Gb. It's there between sd2 & sda3. I just can't get the Live CD to install to it.
 
```
ubuntu@ubuntu:~$ sudo sfdisk -luB
 
Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 1024 bytes, counting from 0
 
Device Boot Start End #blockss Id System
/dev/sda1 * 1024 204799 203776 7 HPFS/NTFS
/dev/sda2 204800 158489599 158284800 7 HPFS/NTFS
/dev/sda3 229762048 244091903 14329856 7 HPFS/NTFS
/dev/sda4 244091904 244197559 105656 c W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
 

```
 
I'm attaching a screenshot of the Windows 7 Disk Management window too.

---

### Post by westie457 on 2011-09-12
Hello.
The screenshot is showing 4 primary partitions. That is why you cannot use the unallocated space.

You have to lose one of the first 4 and my suggestion is to remove the HP Tools partition. That one only contains Windows Drivers and HP Apps that can be downloaded again from the HP support site.

Once that has gone you will be able to use the space you have already created.

---

### Post by Blasphemist on 2011-09-12
The problem is that you already have the maximum of 4 primary partitions. I'd delete the HP Tools partition and download them from HP just in case you do want them sometime.

Then ubuntu can create an extended partition in the unused space. In it a logical partition will be created for / (root) which will include all files for ubuntu and also a logical swap partition.

---

### Post by IrrationalIntellect on 2011-09-13
Thanks westie457 and Blesphemist. This is what the problem was. Didn't know there was a limit for primary partitions and that I was at it.
 
Got it installed and will be doing updates tonight....

---

