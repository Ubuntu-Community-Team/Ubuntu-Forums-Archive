---
title: "Ubuntu installer doesnt see SSD, Windows and Debian Do"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by Jayock on 2010-12-08
After a couple of great builds with an SSD/platter drive combo, I decided to upgrade my home machine with an SSD.  I got an A-Data S599 on a great sale.  If it makes a difference it uses the Sandforce SF-1200 controller.  

On this particular machine, the Ubuntu installer refuses to see the SSD, but only the spinning disk.  I can see the SSD in BIOS, and in the disk utility, but GParted and the Ubuntu installer refuse to see it.  I have successfully installed WIndows and Debian to this drive, so it is accessible in this machine.  Anyone have any ideas for fixing or additional troubleshooting of this issue?

I have tried both the server and desktop media, 32 and 64 bit.  All 10.10.  None work.

---

### Post by ronparent on 2010-12-08
I have the same problem with an ssd. Since I'm not using it for Ubuntu I haven't bothered to chase it down. But I believe from some other post that the issue is that ssd's often need to be aligned for use in installing Ubuntu/Linux. My understanding is that if properly aligned the drives are perfectly usable with Linux OS's.

---

### Post by Reginuse on 2010-12-15
I had a similar problem today. I installed ubuntu 10.10 to a conventional drive. Then used it to partition a SSD drive with fdisk and formatted ext4. Then tried a fresh install to the partitioned SSD. The install failed trying to get to the partition screen. Seemed to be a parted_server failure. If I remove the SSD from the machine the install can advance.

 I can mount and read/write to the drive partitions using the ubuntu 10.10 that is installed on the convention disk but the install can't handle it. 

I am going to try reformatting the SSD using cfdisk and/or gparted if they offer some alignment control. Failing that will try with all the partitions/data removed from the drive. If that works, decide whether to live without the partitions being aligned or just run off the conventional drive.

---

### Post by Reginuse on 2010-12-15
After rereading the original post, I think it is describing a different problem, but just to follow up. 

My issue was the way I had formatted the SSD before install that was not acceptable even though the disk seemed okay being used in a previously installed ubuntu. I think it was causing problems with the partitioning software because the cylinder size was too large. Testing outside the install  using gparted seemed to indicate the default 63*255*512 is the maximum. That might be what caused the failure in the install.
 
I repartitioned using fdisk -H 64 -S 32 this time using cylinder units and not doing anything special for alignment except to start on cylinder 2 to get the first used partition on a 2048 sector boundary.

---

### Post by efflandt on 2010-12-15
I have not had any problems with an Intel SSD using **sudo fdisk -H 32 -S 32** initially and starting on cylinder 2.  You can format partitions with gparted or install iso, but if you change any partitions with gparted, it changes partition table geometry to 255 heads, 63 sectors and however many cylinders that works out to.  I had maverick on it before, currently running natty because updates go more than 10 times faster than on cheap 8 GB USB stick.

```
sudo fdisk -l /dev/sdb

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
32 heads, 32 sectors/track, 152638 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006a571

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2      152638    78150144   83  Linux


sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
32 heads, 32 sectors/track, 152638 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006a571

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1024   156301311    78150144   83  Linux

```It is ext4 with journal disabled.  If your drive has TRIM, the discard option in fstab enables that for ext4 in 2.6.33 or later kernel:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e70810eb-379d-4f9f-9087-54c2f1cd96f9 /               ext4    noatime,discard,errors=remount-ro 0       1
tmpfs        /tmp        tmpfs    defaults    0    0
```

---

### Post by Reginuse on 2010-12-16
Thanks for that, especially the reminder about the trim. 32x32 seems to be most recommended and  224x56 is proposed. When I partitioned the drive under Windows 7 it aligned the first partition on a 2048 sector so I used 64x32. 

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
64 heads, 32 sectors/track, 114473 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1edebd86

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2         514      525312   83  Linux
/dev/sdb2             515       20995    20972544   83  Linux
/dev/sdb3           20996       72196    52429824   83  Linux
/dev/sdb4           72197      114473    43291633    5  Extended
/dev/sdb5           72197       82437    10486768   83  Linux
/dev/sdb6           82438       92678    10486768   83  Linux
/dev/sdb7           92679      114473    22318064   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
64 heads, 32 sectors/track, 114473 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1edebd86

Device      Boot      Start         End            Blocks        Id  System   
/dev/sdb1   *             2048      1052671        525312   83  Linux
/dev/sdb2           1052672     42997759    20972544   83  Linux
/dev/sdb3         42997760   147857407    52429824   83  Linux
/dev/sdb4       147857438   234440703    43291633    5  Extended
/dev/sdb5       147857440   168830975    10486768   83  Linux
/dev/sdb6       168831008   189804543    10486768   83  Linux
/dev/sdb7       189804576   234440703    22318064   83  Linux

---

