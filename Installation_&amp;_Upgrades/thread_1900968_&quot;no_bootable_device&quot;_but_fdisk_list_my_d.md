---
title: "&quot;no bootable device&quot; but fdisk list my drives"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by gfirst on 2011-12-27
on boot my pc says "no bootable device" insert and press any key.
using a live cd, i did 'sudo blkid' and got only '/dev/loop0'.
but when i did 'fdisk -l' i got:
"qimo@qimo-live:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb778d9c5

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       41017   329465857    f  W95 Ext'd (LBA)
/dev/sda2   ?       41017       60599   157286400    7  HPFS/NTFS
/dev/sda5           12401       26124   110237096+  83  Linux
/dev/sda6   *           1        2612    20971520   83  Linux
/dev/sda7           26125       27369     9999360   83  Linux
/dev/sda8           27370       31104    29999104   83  Linux
/dev/sda9           31104       37329    49998848   83  Linux
/dev/sda10           2612        9139    52428800   83  Linux
/dev/sda11          37329       41017    29627392   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2027 MB, 2027945984 bytes
255 heads, 63 sectors/track, 246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c5464

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         246     1975963+  83  Linux
"

what can i do. i think i have to restore my mbr or restore my partition table.

please help me

---

### Post by darkod on 2011-12-27
You can use fixparts or testdisk to sort out the partition table.

Something is confused with sda2. According to the start-end sectors from fdisk, sda2 is inside the extended partition sda1. But in that case it wouldn't be called sda2 because 1-4 is designated for primary partitions, and 5+ for logical.

Also you might reconsider having only logical partitions on the disk and no primary. I don't know if it matters, but the extended partition is a last option when needing more than 4 partitions. It doesn't mean you shouldn't have 3 primary first, before you started thinking about extended partition.

---

### Post by oldfred on 2011-12-27
There are a few BIOS (most Intel motherboards) that have to have the boot flag on a primary partition to let you boot at all. Basically it assumes Windows as that is a Windows requirement, but grub does not use nor need a boot flag.

---

### Post by darkod on 2011-12-27
I have to correct myself, the numbers are not lined up and I didn't see it right.
sda2 does seem to be outside, after sda1 but the fdisk message (one of them) is still "this doesn't seem like partition table". There is something wrong with the table it seems.

On top of it, as oldfred says, the boot flag is on sda6 and needs to be on a primary partition. Set it on sda2, linux doesn't care about boot flag anyway.

---

