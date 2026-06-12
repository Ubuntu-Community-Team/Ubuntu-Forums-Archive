---
title: "annoying partitions"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by ..sam.. on 2010-11-21
Hi,
I am trying to install 10.10 on my new laptop running along side windows 7. 
I have 2 partitions, system and C; on windows 7 and am installing using an Ubuntu CD and pick the alongside option and select the room I want with the slider.
All goes well.

However, in the Computer section once installed I have the system partition, File system and an 80gb section call 80gb file system. 

Is there a way to consolidate the 80gb one into just file system? So I am left with just system (from windows 7 im guessing) and File System?

Much appreciated.

---

### Post by dino99 on 2010-11-21
here is how the partitions might be:

use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by coffeecat on 2010-11-21
> **..sam.. said:**
> However, in the Computer section once installed I have the system partition, File system and an 80gb section call 80gb file system. 

Is there a way to consolidate the 80gb one into just file system? So I am left with just system (from windows 7 im guessing) and File System?

By 'Computer' I presume you mean in Ubuntu not Windows 7. The '80GB' will be a partition without a partition label, but it will not be clear what OS that belongs to. The Ubuntu 'Computer' window will display all your available partitions, your CD/DVD and floppy drives (if present) and 'File System' which is not necessarily a single partition, but your whole Ubuntu filesystem (which can be on one or more partitions). It is a bit of a mish-mash but comprehensible when you get used to it.

So that we can see what your partition layout is really like, in Ubuntu open a terminal (Applications > Accessories) and post the output of:

```
sudo fdisk -lu
```If you don't understand the  output I'll interpret it for you. If you want to see it graphically, you can open System > Administration > Disk Utility and click on your main hard drive. If you look in Disk Management in Windows you'll see a simplified partition layout so it's better we look at the way Ubuntu presents it.

---

### Post by sikander3786 on 2010-11-21
Ubuntu is already installed as I understand from you post (??).

Please post the output of

```
sudo fdisk -lu
```

It would give the information about exact partition setup on your computer.

**[COLOR="Red"]Edit:[/COLOR]** **coffeecat** beats me here :-)

---

### Post by ..sam.. on 2010-11-21
Thank you both,
here is the info:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3441d854

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          409600   156682967    78136684    7  HPFS/NTFS
/dev/sda3       156684286   976771071   410043393    5  Extended
/dev/sda5       156684288   952199167   397757440   83  Linux
/dev/sda6       952201216   976771071    12284928   82  Linux swap / Solaris


It all just seems a bit messy to me and the 80gb part is just taking up room if nothing is going to be installed on it and is too small if it is.

Thanks.

---

### Post by sikander3786 on 2010-11-21
I couldn't find anything wrong with your partition table. I think the answer lies here, posted by **coffeecat**,

> The Ubuntu 'Computer' window will display all your available partitions, your CD/DVD and floppy drives (if present) and 'File System' which is not necessarily a single partition, but your whole Ubuntu filesystem (which can be on one or more partitions). It is a bit of a mish-mash but comprehensible when you get used to it.

You've got a [s]20GB[/s]it is 200MB actually NTFS sda1, 80GB NTFS sda2, 400GB sda3 Extended Partition which contains sda5 Linux Root partition and a Swap sda6 partition.

Which 80 GB partition you think is offensive?

---

### Post by ..sam.. on 2010-11-21
hahaha, sorry, it all makes sense now.
The 80gb is the windows 7 partition....system is system and the big one is ubuntu....
sorry it was just me not connecting the dots.
Thank you very much.

Is there a way to hide the system and windows 7 drives?

---

### Post by coffeecat on 2010-11-21
Your 80GB partition is your Windows C: partition, so you cannot consolidate that into your Linux system. Here is what the important bits of that output mean. I'll give sizes in GB (gigabytes) which are base 10 and GiB (gibibytes) which are base 2.

sda1 = approx 200 MB. A primary partition with the boot flag set. This is your Windows 7 boot partition.

sda2 = 80GB, 74.5GiB. A primary partition. This is your Windows C:

sda3 is an extended partition which is a "container" for the remaining logical partitions.

sda5 = 407.3GB, 379.3GiB. This is a logical partition, your Ubuntu root (/) partition.

sda6 = 12.6GB, 11.7GiB. This is a logical partition, your Ubuntu swap partition.

Everything is OK. The only comment I'll make is that your Ubuntu root partition is vast. You might want to consider creating a separate data partition to be used by both Ubuntu and Windows. If you want more details, post back. Also - your swap partition is generous. How much RAM do you have?

---

### Post by ..sam.. on 2010-11-21
4gb of ram...i think.

---

### Post by coffeecat on 2010-11-21
> **..sam.. said:**
> 4gb of ram...i think.

The old rule-of-thumb was 2x your system RAM, but that was in the days when RAM was measured in MB, not GB. The more RAM you have the less the system will access swap. If you need hibernation you need swap at least equal to your RAM, otherwise not. On my 4GB RAM system I've set up a swap of 4GB in case I might need to use hibernation, but in routine use the swap is rarely used at all - if ever. Whatever - 12GB is probably doing no harm but if you want to do a bit of rearrangement of your partitions, you could probably recover about 8GB from that without detriment.

> **..sam.. said:**
> Is there a way to hide the system and windows 7 drives?

Offhand, I can't think of a way, but sikander3786 might know.  :p

---

### Post by sikander3786 on 2010-11-21
> Offhand, I can't think of a way, but sikander3786 might know.

Unfortunately, I don't either :P

But, man udev might give a pointer how to achieve that.

```
man udev
```

---

### Post by ..sam.. on 2010-11-22
Thank you all very much for your help.
Its much appreciated.

---

