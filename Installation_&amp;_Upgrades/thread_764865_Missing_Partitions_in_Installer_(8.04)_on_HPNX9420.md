---
title: "Missing Partitions in Installer (8.04) on HPNX9420"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by lephisto on 2008-04-24
Hello,

I try to install the Ubuntu 8.04 LTS on my Notebook (HP NX9420).

Unluckily, when the Installer starts and Step4 (Partitioning) occurs, it doesn't display my Partitions. I just have the option to use the whole HDD (which i won't try ;)).

When i switch to the Console with ALT-F2 and use "sudo fdisk /dev/sda" followed by "p" - it does show me my Partitions.

Any Ideas?

mephisto

---

### Post by Pumalite on 2008-04-24
If you have Vista; use Vista partitioner. If you have XP; use Gparted Live CD and 'shrink' XP.

---

### Post by lephisto on 2008-04-24
First, the primary OS is XP, not Vista.

That's not the problem anyways - I already have the System partitioned from a previous Linux install. BUT - if the (existing) Partitions don't appear in the Partitioner of the installer, i cannot chose them as Rootfilesystem, eh?

mephisto

---

### Post by Pumalite on 2008-04-24
Do you have the option to go 'Manual'?

---

### Post by lephisto on 2008-04-24
Yes, I can go "manual" - but then it doesn't respect my current partitioning and presents my HDD as it would hold no partitions at all. (there are 4: WINDOWS, RECOVERY, Linux / and Linux Swap).

But I need to preserve my Windows system and just delete the existing Linux/Swap Partition and re-use it for hardy.

mephisto

---

### Post by Pumalite on 2008-04-24
It could be a bad burn. Burn a new CD. Do md5sum, burn at 4x or less, check CD integrity after burn. Use CD-R. Clean the lens in your burner. Try your CD's in diferent computers.

---

### Post by lephisto on 2008-04-24
Checking that.

MD5 was corrent. Now burning with 10x (the lowest speed my writer does ;I)

thanks, so far.

mephisto

---

### Post by lephisto on 2008-04-24
//Update:

Checked CD, re-burned, remade ISO to check MD5: OK

Still the same effect - when i choose "manual", it just shows me /dev/sda in the listing as if there was no partition at all.

One thing that makes me a bit susicious when i view the Partition with fdisk:

> 
bma@fsisp:~> more fdisk.txt

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0c9b0c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9656    77558008+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           11137       12161     8232808+   c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            9656       11071    11374020   83  Linux
/dev/sda4           11072       11136      522112+   5  Extended
/dev/sda5           11072       11136      522081   82  Linux swap / Solaris

Partition table entries are not in disk order


Can this cause an exception in the Graphical Partitioner? cfdisk won't work either.

lephisto

---

### Post by Pumalite on 2008-04-24
You could have a Partition Table problem. Check with TestDisk: 
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Drone4four on 2008-04-25
We're arm wrestling with a very similar problem in this thread here:
[http://ubuntuforums.org/showthread.php?p=4790067&posted=1#post4790067](http://ubuntuforums.org/showthread.php?p=4790067&posted=1#post4790067)

---

### Post by mailforbiz on 2008-04-30
I have the exact same problem. When the partitioner loads, it just brings up my hard disk (/dev/sda) with just the Create Partition button highlighted. It seems to think there are no partitions on it. I obviously don't want to wipe out the whole drive. Any resolution yet?

---

### Post by mailforbiz on 2008-04-30
> **mailforbiz said:**
> I have the exact same problem. When the partitioner loads, it just brings up my hard disk (/dev/sda) with just the Create Partition button highlighted. It seems to think there are no partitions on it. I obviously don't want to wipe out the whole drive. Any resolution yet?

It seems there is some issue in the partition table:

Testdisk reports
Space conflict between the following two partitions
 4 E extended LBA         15507   0 62 24321  41 40  141599472
 1 P FAT32 LBA            23994 238 53 24321  41 40    5240832 [MEDIADIRECT]

How does one resolve this?

I think I have the following partitions:

Dell Utitility
Dell Mediadirect
Vista (two logical partitions)
Ubuntu

Thanks!

This is the entire display of Testdisk
Disk /dev/sda - 200 GB / 186 GiB - CHS 24322 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P FAT32 LBA            23994 238 53 24321  41 40    5240832 [MEDIADIRECT]
 2 * HPFS - NTFS             10  18  9  7857  26 41  126062592
 3 P HPFS - NTFS           7857  26 42 15506   7 53  122880000 [Data]
 4 E extended LBA         15507   0 62 24321  41 40  141599472
Space conflict between the following two partitions
 4 E extended LBA         15507   0 62 24321  41 40  141599472
 1 P FAT32 LBA            23994 238 53 24321  41 40    5240832 [MEDIADIRECT]
 5 L Sys=DD               23994 238 53 24321  41 40    5240832
   X extended             15507   0 63 15848 254 63    5494168
 6 L Linux Swap           15507   1  1 15848 254 63    5494167
   X extended             15849   0  1 18280 254 63   39070080
 7 L Linux                15849   1  1 18280 254 63   39070017
   X extended             18281   0  1 23750 254 63   87875550
    Next
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

---

### Post by Pumalite on 2008-04-30
If you are running XP, get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Post screen shot of Gparted

---

### Post by louieb on 2008-04-30
> **lephisto said:**
> I already have the System partitioned from a previous Linux install. 
Just wondering if the previous Linux was PCLinuxOS or Mandrivia. Or if you have used the DiskDrake partitioner?  fdisk shows sda1 and sda3 overlap at   9656.
```

/dev/sda1   *           1        9656    77558008+   7  HPFS/NTFS
/dev/sda3            9656       11071    11374020   83  Linux

```

This is an invalid  partition table and GParted and the Ubuntu installer partitioner sees that and says unt ua I ain't doing anything. Might try to fix it with DiskDrake.

---

