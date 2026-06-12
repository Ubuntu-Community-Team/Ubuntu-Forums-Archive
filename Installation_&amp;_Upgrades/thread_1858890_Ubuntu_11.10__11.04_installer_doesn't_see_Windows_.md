---
title: "Ubuntu 11.10 / 11.04 installer doesn't see Windows installations!"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by ivarzLV on 2011-10-13
Hi, yesterday I downloaded Ubuntu 11.10 RC DVD, burned into DVD disc and tried to install. At this moment on my PC are two OS - OpenSuSe and Windows 7.

When Ubuntu installation comes to step where I need to choose to install along Windows installation or format all HDD, it shows only "Erase everything" and "Something Else". 

Even if I choose "Something Else" installer doesn't recognise any of my existing operating systems. Any ideas about this? :(

---

### Post by katya_sehgal on 2011-10-13
same issue. see if descriptions here may help.

[http://ubuntuforums.org/showthread.php?t=1858322](http://ubuntuforums.org/showthread.php?t=1858322)

---

### Post by Quackers on 2011-10-13
Are there already 4 primary partitions in use on the system?
Is there any empty space on the hard drive (not empty space inside a partition)?

---

### Post by ivarzLV on 2011-10-13
> **Quackers said:**
> Are there already 4 primary partitions in use on the system?
Is there any empty space on the hard drive (not empty space inside a partition)?

There are three partitions for Win (C, System Reserved and D), one partition for OpenSuSe = yes, there already are 4 partitions. 

And no, there isn't any empty space on HDD. Maybe it could help if I just delete partition with OpenSuse installation? I have a backup and I don't need it anymore - of course if it can help!

---

### Post by Quackers on 2011-10-13
If all your current partitions are primary partitions you will not be able to install Ubuntu - even if you create some free space.
You will first need to delete one of the primary partitions. You can then do one of two things.
You can let Ubuntu install into that free space (which will create a swap partition and an Ubuntu root partition which will both be logical partitions housed inside a new extended partition.
Once that is done you can have as many logical partitions (NOT primary partitions) as you want inside that extended partitions.

OR

You can manually create an extended partition in the new free space.
This new extended partition can hold as many logical partitions as you want.
Most Linux systems will boot from a logical partition, whereas Windows won't boot from a logical partition unless its boot files are in a separate primary partition.

If you choose the second method you can install Ubuntu manually by selecting the "something else" option and choosing your new logical partitions to install into.

---

### Post by ivarzLV on 2011-10-13
I'm just thinking why installator don't show any installed operating systems anyway ..

---

### Post by Quackers on 2011-10-13
Because the installer knows there is nowhere for it to install Ubuntu to. If it showed you what was there you may be tempted to create more partitions ;)
It's safer if you can't do that.

---

### Post by gauravbutola on 2011-10-20
> **Quackers said:**
> Because the installer knows there is nowhere for it to install Ubuntu to. If it showed you what was there you may be tempted to create more partitions ;)
It's safer if you can't do that.

I am pretty sure it's a bug, not feature. I am facing the same issue, I only have one partition (for windows) but still installer doesn't detect Windows, and when trying to create partitions manually, It shows my whole HDD as un-partitioned. Disk Utility does indeed detect the Windows partition. 
It definitely is a bug in ubiquity.

I even wiped my whole hard disk then installed Windows and then tried to install Ubuntu but still, same problem.

---

### Post by pritam_par on 2011-10-25
It will not show Operating systems names but will show the drive in which they are installed 
like /sda1, /sda2 etc you can identify your OS drive by its size only.

___________________________________________________________________________

---

### Post by Mark Phelps on 2011-10-26
> **gauravbutola said:**
> I even wiped my whole hard disk then installed Windows and then tried to install Ubuntu but still, same problem.

If you installed Windows 7 to an unformatted drive, then you have TWO partitions.  Why? Because Win7, when installed to an unformatted drive, automatically creates a 100MB partition in front of the Win7 OS partition.

If you're running Win7, you should open the Win7 Disk Management utility to see what it sees on your drive.

---

### Post by Hakunka-Matata on 2011-10-26
Please post output of ```
sudo fdisk -l
```

---

### Post by murthy on 2011-10-28
I am also facing the same problem, while trying to install from Live USB. I have 2 HDs (1TB and GB), with win 7 installed in HDD1. Xubuntu does not recognise the partitions on HDD1, It has only 2 primary partitions and 3 extended partitions and intend to install xubuntu to one of the extended partitions. Xubuntu only shows the partitions on HDD2. Xubuntu shows my whole HDD1 as un-partitioned. Disk Utility detects all the Windows partitions in HDD1.
 
fdisk -l gives the following output:
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b8372

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 206847 102400 7 HPFS/NTFS/exFAT
/dev/sda2 206848 419637247 209715200 7 HPFS/NTFS/exFAT
/dev/sda3 419637248 1953516911 766939832 5 Extended
/dev/sda5 419639296 1258500095 419430400 7 HPFS/NTFS/exFAT
/dev/sda6 1258502144 1782790143 262144000 7 HPFS/NTFS/exFAT
/dev/sda7 1782792192 1953523711 85365760 7 HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000488b6

Device Boot Start End Blocks Id System
/dev/sdb1 63 167766794 83883366 7 HPFS/NTFS/exFAT
/dev/sdb2 167766856 976771071 404502108 5 Extended
/dev/sdb5 167766858 587191814 209712478+ 7 HPFS/NTFS/exFAT
/dev/sdb6 587191878 976771071 194789597 7 HPFS/NTFS/exFAT

---

