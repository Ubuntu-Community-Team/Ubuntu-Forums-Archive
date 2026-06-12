---
title: "Mount existing RAID"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by andersv2 on 2013-10-14
Hi there.
Newly registered user, although not totally new to Linux. I apologize if this question is posted somewhere else - I was unable to formulate a relevant search string applicable to my situation.

I'm running a stripe-raid(RAID0) with 4 SSD's on my onboard SATA-controller(Z87-chipset on Asus VI Hero MB), which was formatted and mounted on my win8 - NTFS formatted as dynamic disk.
I would really like to at least get read-support on this volume while in my Ubuntu(13.04) - if possible, without formatting the volume.

Any suggestions on how I would go about doing this?

My fdisk shows the four disks like this. This is the output:
```

Disk /dev/sdc: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x8107bf16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63        2047         992+  42  SFS
Partition 1 does not start on physical sector boundary.
/dev/sdc2   *        2048      718847      358400   42  SFS
/dev/sdc3          718848  4000839679  2000060416   42  SFS
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xc1e4 of partition table 5 will be corrected by w(rite)

Disk /dev/sdd: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00015124

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048      499711      248832   83  Linux
/dev/sdd2          501758   389543935   194521089    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdd3       389564416   998846463   304641024   83  Linux
/dev/sdd5   ?  1150258047  2989323131   919532542+  f3  Unknown
Partition 5 does not start on physical sector boundary.
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x47aa of partition table 5 will be corrected by w(rite)

Disk /dev/sde: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b3dd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048      499711      248832   83  Linux
/dev/sde2          501758   389543935   194521089    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sde3       389748736   999030783   304641024   83  Linux
/dev/sde5   ?    87815812   741585116   326884652+   d  Unknown
Partition 5 does not start on physical sector boundary.
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xb212 of partition table 5 will be corrected by w(rite)

Disk /dev/sdf: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b3dd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        2048      499711      248832   83  Linux
/dev/sdf2          501758   389543935   194521089    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdf3       389748736   999030783   304641024   83  Linux
/dev/sdf5   ?      845370  2549862864  1274508747+  46  Unknown
Partition 5 does not start on physical sector boundary.

```

Thanks so much.
/Anders

---

