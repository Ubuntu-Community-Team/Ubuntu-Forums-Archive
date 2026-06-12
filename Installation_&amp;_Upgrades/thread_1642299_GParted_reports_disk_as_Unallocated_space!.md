---
title: "GParted reports disk as Unallocated space!"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by Dr.Fuzzy on 2010-12-10
Although I've seen several threads with the same problem, I have not managed to solve the problem. GParted identifies my /dev/sda as unallocated disk space! The machine a Dell Inspiron M101Z laptop running Ubuntu 10.10 32 bit + W7 64 bit. I wouldn't have discovered the problem until I decided to replace my 32 bit Ubuntu with the 64 bit version, then GParted from the live cd identified my drive as Unallocated space!

I've already tried to use testdisk to write the partition table, but though it writes the table successfully and then it prompts to reboot, GParted still sees it as Unallocated. I've also tried fdisk /dev/sda then p then w to write the partition table, but again GParted screws up for some reason and sees it as Unallocated.

sudo fdisk -l -u

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83fc49c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80321       40129+   6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sda2           81920    30801919    15360000    7  HPFS/NTFS
/dev/sda3   *    30801920   196728066    82963073+   7  HPFS/NTFS
/dev/sda4       196728084   488408129   145840023    f  W95 Ext'd (LBA)
/dev/sda5       196728832   476469247   139870208   83  Linux
/dev/sda6       476471296   488396783     5962744   82  Linux swap / Solaris

```I'm desperate...what the heck is happening? Any ideas?

---

### Post by Dr.Fuzzy on 2010-12-11
Anyone?

---

### Post by coffeecat on 2010-12-11
> **Dr.Fuzzy said:**
> Anyone?

Yes.

Here's your problem:

> **Dr.Fuzzy said:**
> ```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total [COLOR=Red]488397168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83fc49c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80321       40129+   6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sda2           81920    30801919    15360000    7  HPFS/NTFS
/dev/sda3   *    30801920   196728066    82963073+   7  HPFS/NTFS
/dev/sda4       196728084   [COLOR=Red]488408129[/COLOR]   145840023    f  W95 Ext'd (LBA)
/dev/sda5       196728832   476469247   139870208   83  Linux
/dev/sda6       476471296   488396783     5962744   82  Linux swap / Solaris

```

The partition table is showing the extended partition as ending on a sector beyond the physical end of the drive. Here's the explanation and fix:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

With thanks to forum member srs5694. It seems that testdisk does this quite often. It did it to me. If you need any help with the instructions in that link, do post back.

---

### Post by Dr.Fuzzy on 2010-12-11
Man you are a star! 5 mins to read it, one subtraction, and job's done!!! Many many thanx! I can happily install the 64 bit version now!:D

---

### Post by coffeecat on 2010-12-11
Good luck! :)

---

### Post by Dr.Fuzzy on 2010-12-11
Up and running the 64 bit version! Thanx a million! :popcorn:

---

