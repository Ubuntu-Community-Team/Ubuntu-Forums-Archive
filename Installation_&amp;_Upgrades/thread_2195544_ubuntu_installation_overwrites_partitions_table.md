---
title: "ubuntu installation overwrites partitions table"
date: 2013-12-24
forum: Installation &amp; Upgrades
---

### Post by mrmaxpires on 2013-12-24
Hi guys, I think i am in a big trouble..

I had a 640GB hard drive partitioned as follow:    |10GB (recovery) unused | 100GB windows 7| 450GB DATA | 40GB unused |
I was trying to install ubuntu in the last piece of hd, but in the instalation setup i selected whole disk wrongly. But right in the beggining of instalation I realize it and stop it, but it was late. My Windows dont boot anymore and I lost the other partitions. Ubuntu and windows instalation setup show only one partition when i'm trying to reinstall.

now i booting by ubuntu liveCD (usb stick) and i think i can recover all partitions, look the fdisk -l, called from live ubuntu:
```

# fdisk -l
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00053d57

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1241913343   620955648   83  Linux
/dev/sda2      1241915390  1250263039     4173825    5  Extended
/dev/sda5      1241915392  1250263039     4173824   82  Linux swap / Solaris

Disk /dev/sdb: 8032 MB, 8032092160 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdb2   ?  3272020941  5225480974   976730017   16  Hidden FAT16
/dev/sdb3   ?           0           0           0   6f  Unknown
/dev/sdb4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order

```

searching on web, people say that it is possible to recover the partitions table with testdisk, i'm trying that, but i'm not sure it will help. i perform two deep-searches and the result was follows:

```

  Linux                    0  32 33 77305 135 14 1241911296
  Linux                    0  32 33 77305 135 14 1241911296
  HPFS - NTFS              0  32 33  1312 109 13   21082112 [Recovery]
  HPFS - NTFS           1312 109 14  1325  44 63     204800
  HPFS - NTFS              0  32 33  1312 206 46   21088256 [Recovery] <<<<< i think it is the 10GB partition
  HPFS - NTFS           1312 206 47  1325 142 33     204800 [Reservado pelo Sistema]
  Linux                    0  32 33 77305 135 14 1241911296
  HPFS - NTFS           1312 206 47  1325 142 33     204800 [Reservado pelo Sistema]
  HPFS - NTFS           1325 142 34 14061   5 24  204595200
  Linux                    0  32 33 77305 135 14 1241911296
  Linux                    0  32 33 77305 135 14 1241911296
  Linux                    0  32 33 77305 135 14 1241911296
  Linux                    0  32 33 77305 135 14 1241911296
  Linux                    0  32 33 77305 135 14 1241911296
  HPFS - NTFS           1325 142 34 14061   5 24  204595200  <<< i think it is the 100GB partition
  HPFS - NTFS          14061   5 25 72596 253 62  940380437 <<<  450GB partition

```

I choose one before, but didnk work... i dont remember the result.. will do asap and edit here..
result:

```

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 640 GB / 596 GiB - CHS 77825 255 63

The harddisk (640 GB / 596 GiB) seems too small! (< 1078 GB / 1004 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
>  HPFS - NTFS          72596 254 63 131132 248 37  940380437

```

Do anyone know what to do in this situation?

thanks
best regards
Max

---

### Post by ubfan1 on 2013-12-24
From the live media, you can just recreate the partition table, using the sizes you originally had (best if you had previously written down the exact block start/end, but even your rough sizes might be sufficient).  Then the recovery tools might stand a better chance.  If you're lucky, you might even have a whole Windows system again -- if not try chkdsk on what you do have.

---

### Post by mrmaxpires on 2013-12-24
> **ubfan1 said:**
> ...you can just recreate the partition table, using the sizes you originally had (best if you had previously written down the exact block start/end, but even your rough sizes might be sufficient).

do you know how to do this? could you show me?

thank you very much for your attention...

---

### Post by mrmaxpires on 2013-12-24
Note that the second part of the fdisk output, refer to my USB stick, with ubuntu liveCD.

Disk /dev/sdb: 8032 MB, 8032092160 bytes

---

### Post by mrmaxpires on 2013-12-24
Trough testdisk i can see the files after selection the partitions that was found by deeper-search, windows and data files.. all there, i junt need to remount their partition to get access.
i added them with A key, but at the end comes a message saying that no partition was selected for recover, or something like that.. big problems now, because i need to analyse all disk again to go to that page again..

---

### Post by ubfan1 on 2013-12-24
Well, fdisk can remake your partition table.  run it with sudo
sudo fdisk
type m for help
type p to print the existing partition table (probably bad)
type d to delete bad partitions,
type n to create a new partition, then select p for primary, and now guess the start (same as default?), guess the size as what you said, make them in order, when all done with the first partition, make the next, then then next.
when done, w to write out the new table.
You can then try mount read only the new partitions, and see if you can see any files.  You can redo the partition table with different sizes if you think it will help.
Write nothing else onto the data part of the disk yet.  When  your partition table is as good as you can make it, then you can try some recovery tools, or just copy off what you see.
If you have the space, you can just take a block copy of the entire disk, just in case the recovery goes badly, and you want to try again.

Good luck.

---

### Post by oldfred on 2013-12-24
From testdisk you need to select a set of partitions that do not overlap. It shows starts & ends and sizes but shows mulitples for each time something changed. 
Windows also has a hidden 100MB boot partition shown as Reservado pelo Sistema with 204800 or about the typical 100MB. I would recover that also.

It will depend a lot on what was written or if it was just partition table on what you can recover.
But testdisk uses the old CHS cylinders, heads, sectors that have not been used for years. but it is some math to convert to the sectors with Large block allocation now used.
 Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

---

### Post by mrmaxpires on 2013-12-25
thank you all guys..
I did it!! 
Testdisk really solved the problem.. I didnt know how to use it, but after a few tries I got.. (use arrows to select partion type, boot and primary partition)
After all, testdisk shows you all the partitions it found in HD, so you can rewrite all partition table again.. 
It was bad and good, bad because I lost some time and thought that I had lost all files. But was good because i learned about partitions table, system boot and of course how to use testdisk.

thanks
BR
Max

---

