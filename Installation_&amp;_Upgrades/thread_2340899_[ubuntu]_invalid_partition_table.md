---
title: "[ubuntu] invalid partition table"
date: 2016-10-23
forum: Installation &amp; Upgrades
---

### Post by pael2 on 2016-10-23
Hi guys,

I know topic was before but I will be very greatful to do it step by step with me in order not to lose any data... 

I started with 

```
sudo fdisk -l
```


```
Disk /dev/loop0: 1.2 GiB, 1246838784 bytes, 2435232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 4E26783C-2BB9-4F5F-824B-45681A6A0C36

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624   2050047    999424   488M Linux filesystem
/dev/sda3  2050048 500117503 498067456 237.5G Linux filesystem


Disk /dev/sdb: 14.9 GiB, 16008609792 bytes, 31266816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0008f854

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 31266815 31264768 14.9G  c W95 FAT32 (LBA)


```

I stopped instalation of ubuntu-gnome 16.10 and can't boot older partions now. 
Is there a way to reload previous boot configuration or get access to data at least ?...


Huge thanks in advance...

edit:

```

TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 256 GB / 238 GiB - CHS 31130 255 63
     Partition               Start        End    Size in sectors
>* FAT32                    0  32 33    65 101 36    1048576 [NO NAME]
 P Linux                   65 101 37   127 155 28     999424
 P Linux                  127 155 29   127 220 29       4096
 L Linux                 5333 249 37  7357  63  2   32503808
 L Linux                12898 163  2 13812  77 25   14678016
 L Linux                14026  23 14 18889  38 29   78125056
 L Linux Swap           18889  70 62 19147 142  3    4149248
 L Linux                19147 174 36 31130 223  5  192509952




```

it is more or less what was before

---

### Post by TheFu on 2016-10-23
Make a bit-for-bit backup to another disk - that is step 1.

Have you run **boot-repair** or **update-grub**?

---

### Post by pael2 on 2016-10-23
I tried with no success.
I can access data from partition with data, I am afraid the only way is to copy files one by one and then format whole disk...

I will wait if someone has better idea if not... :)

---

### Post by TheFu on 2016-10-23
What, exactly, did you try? Can't read minds here. ;)

---

### Post by pael2 on 2016-10-23
Well, I do not what I changed in mean time but I've tried install once again and it could have been install besides old linux :-)... I lost windows and have plenty of strange partitions but it is not important :D ... I will clean it up later after EXTERNAL backup...

---

### Post by oldfred on 2016-10-23
Your testdisk with logical outputs must have been BIOS/MBR configuration.
But current partitions are UEFI/gpt which totally removed all the MBR partitions.

If you recover MBR partitions, you will erase gpt, but do not expect to recover everything as at least parts of drive were overwritten with new install.
If testdisk's deeper search shows files that is best way to recover files as then it includes file names. Using photorec can potentially recover more files, but will not nave file name just extension.

---

