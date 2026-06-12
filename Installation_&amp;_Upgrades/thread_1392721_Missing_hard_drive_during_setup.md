---
title: "Missing hard drive during setup?"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by BrutalSpoon on 2010-01-28
Hi everybody,

I'm not sure if I'm missing something completely obvious, but I'm having issues installing Ubuntu to one of my drives.

I've managed to get a hold of a 160GB drive, which I hope to use as my system drive for a server that I'm setting up. This may be the tip of the iceberg (as it tends to be with me for some reason), but this is what's happening:

I got the drive, which has been used before but has been secure erased, and it's been sea tool-ed so is therefore as good as new. It shows up fine in the BIOS, and GParted discovers it straight away. I then split it into 3 partitions:

[LIST]
[*]A ~10GB system partition - sdd1
[*]A ~130GB storage partition - sdd2
[*]A ~4GB swap partition - sdd3
[/LIST]

GParted performs all actions straight away with no issues.

After partitioning, fdisk -l reports the following:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13054   104856223+   7  HPFS/NTFS
/dev/sda2           13055       56225   346771057+  17  Hidden HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbda1bda1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121602   976762583+  ee  GPT

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x815a524f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488383488    7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e817

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1305    10482381   83  Linux
/dev/sdd2            1306       18935   141612975   83  Linux
/dev/sdd3           18936       19457     4192965   82  Linux swap / Solaris

```

With sdd being the drive I've just formatted.

I've then gone to install Ubuntu. I go through all the major steps, up to where it asks you where you want to install Ubuntu... at which point sdd just doesn't show up at all. It shows sda, sdb and sdc fine, but sdd is nowhere to be seen.

Two things strike me as odd (although I suppose understandable) - Firstly, every partition in sdd mounts fine, but is owned by root. Secondly, each partition has a folder called 'lost+found' with varying amounts of data. There's 662.3MB in the 10GB partition's lost+found folder, and 6.9GB in the 130GB's folder.

Again, there's every chance that I've missed something completely obvious, so I'd be much obliged if somebody could point me in the right direction.

Thanks in advance (as always),

BrutalSpoon

---

### Post by darkod on 2010-01-28
The most frequent reason a disk not to show in the installer but fdisk and Gparted can see it, is if the disk has raid settings remains on it. Karmic can detect them and gets confused. You don't need to have actual array, settings remains are enough.
But the claim to be secure erased doesn't support this. If you still want to make sure this is not the problem and if you are not running raid on any drives, boot the live desktop and in terminal do:

sudo dmraid -E -r /dev/sdd
sudo apt-get remove dmraid

Reboot and see if the installer can see it now.

Also, since you created partitions in advance, you are aware that you have to use the Manual Partitioning in step 4 right? That is the only way to use existing partitions. You have to select each partition one by one, then hit the button Change at the bottom, and change the filesystem and mount point as necessary.

---

### Post by BrutalSpoon on 2010-01-28
> **darkod said:**
> The most frequent reason a disk not to show in the installer but fdisk and Gparted can see it, is if the disk has raid settings remains on it. Karmic can detect them and gets confused. You don't need to have actual array, settings remains are enough.
But the claim to be secure erased doesn't support this. If you still want to make sure this is not the problem and if you are not running raid on any drives, boot the live desktop and in terminal do:

sudo dmraid -E -r /dev/sdd
sudo apt-get remove dmraid

Reboot and see if the installer can see it now.

Also, since you created partitions in advance, you are aware that you have to use the Manual Partitioning in step 4 right? That is the only way to use existing partitions. You have to select each partition one by one, then hit the button Change at the bottom, and change the filesystem and mount point as necessary.

Well, I was told that the drive was secure erased. I'll try that to see if it works.

Yes, I know about Manual Partitioning. I was planning to have sdd1 set as /, sdd2 as /media/Arcness (strange name, but it fits my drive naming scheme), and swap as... well... swap :P

Thanks for the quick reply :)

EDIT: Looks like it was still allegedly part of an nVidia RAID. Removing it now. I'll let you know how it goes once I reboot :)

EDIT 2: Yep, that fixed it just fine! Thank you very much for your help. Doing the sensible thing and installing it with only this drive in the system so that it's now sda. A gold star for you :D

---

