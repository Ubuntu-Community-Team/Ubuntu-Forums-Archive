---
title: "Advanced Format - 4K Sectors"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by Nadler on 2011-03-19
Just to be sure. I am going to prepare my 2nd disk on PC for multimedia. I will use Seagate Barracuda Green 2TB (ST2000DL003) disk. (my OS: Kubuntu Karmic Koala)
I want to create ext4 partition with live CD - Gparted tool.

Because of using Advanced Format technology (4K sectors) I am not sure how to create partition. 


Should I clear an option "Round to cylinders" and "Free space preceding (MiB)" set to "1"?

Sorry for newbie question.

---

### Post by srs5694 on 2011-03-19
Align all partitions on 8-sector boundaries. The 1 MiB option in recent versions of GParted will do that. (1 MiB is actually 2048 sectors, but since that's a multiple of 8, it'll do the job.) For more details, see [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) that I wrote for IBM developerWorks a while back. Note, however, that the partitioning tools have changed a bit since then, so some of the details vary. I strongly recommend that you verify proper alignment with fdisk (or gdisk or parted):

```

sudo fdisk -lu /dev/sdb

```

Change the device ID as appropriate. Ensure that every partition's start sector number is a multiple of 8.

FWIW, this is the first I've heard of a Seagate Advanced Format disk. I knew they were planning to release such disks, but I didn't realize they were out yet.

---

### Post by Nadler on 2011-03-21
Latest version of Gparted (live CD) has new design against my previous version. 
I have created extended container with ext4 and swap partitions. Parameters were 1MiB ("Free space preceding (MiB)") and Align to MiB as default option. (Available options are Align to MiB, Align to Cylinders, No Aligment). 
 
 
 
```

 
Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004e7b8
 
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907028991  1953513472    5  Extended
/dev/sdc5            4096  3888955391  1944475648   83  Linux
/dev/sdc6      3888957440  3907028991     9035776   82  Linux swap / Solaris
 
 
 

```
 
 
 
Each start sector can be divided by 8 and the result is integer. 
 
 
 
Than I have realized that I don’t need swap partition because this is data disk. 
I have formatted disk and created new partition (with default options, Free space preceding =1MiB and Align to MiB ).
 
 
 
```

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00058ff7
 
 
  Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907028991  1953513472   83  Linux
 

```
 
 
 
Start sector is 2048. 2048/8= 256 so my understanding is that disk was properly aligned and meets Advanced Format standards.
I hope that I am right .. or … ?

---

### Post by srs5694 on 2011-03-21
Yes, that looks fine.

---

### Post by Nadler on 2011-03-22
Thanks for help.

---

