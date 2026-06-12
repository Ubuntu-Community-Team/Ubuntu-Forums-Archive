---
title: "Extend ext4 system partition after installation?"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by KraXarN on 2013-10-27
Hi there!
I installed Ubuntu 13.10 not to long ago just to try it out. I also have Windows 8.1 and I'm dual booting. I thought i wouldn't use Ubuntu so much, but i really like it and it ended up being my main OS. The problem is, when I well installed it, i only gave it 15 GB of my hard drive. Soon after those gigabytes ran out, causing serious graphical glitches. I cleaned some files and now everything works perfect again, but I can't extend the ext4 partition when I boot Ubuntu 13.10 from a USB-Stick. When I resizes my main partition on my hard drive it becomes unallocated, but I can't move the space on my Ubuntu ext4 partition. Can someone please help me? :(

Regards Emil a.k.a. KraXarN

---

### Post by sudodus on 2013-10-28
Welcome to the Ubuntu Forums :-)

We need to see you partition table in order to give relevant advice, so please post the output of the following commands, when booted from the Ubuntu install USB drive

```
 sudo fdisk -lu
```
```
 sudo parted -l
```

It will be easier to read if you 'go advanced', mark the output lines, and click on the # icon at the top of the editing window to put the text within code tags.

---

### Post by KraXarN on 2013-10-28
Thank you!
When i type sudo fdisk -lu, it says:
```
Disk /dev/sdd: 180.0 GB, 180045766656 bytes
255 heads, 63 sectors/track, 21889 cylinders, total 351651888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69f7f859

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   299956223   149977088    f  W95 Ext'd (LBA)
/dev/sdd2   *   299956224   320927743    10485760   83  Linux
/dev/sdd3       320929792   324927487     1998848   82  Linux swap / Solaris
/dev/sdd4       324927488   351651839    13362176   83  Linux
/dev/sdd5            4096   299956223   149976064    7  HPFS/NTFS/exFAT
```

And when I type sudo parted -l, it says:
```
Model: ATA INTEL SSDSC2CT18 (scsi)
Disk /dev/sdd: 180GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  154GB  154GB   extended                  lba
 5      2097kB  154GB  154GB   logical   ntfs
 2      154GB   164GB  10.7GB  primary                   boot
 3      164GB   166GB  2047MB  primary   linux-swap(v1)
 4      166GB   180GB  13.7GB  primary   ext4
```

Hope that helped a bit :)

---

### Post by sudodus on 2013-10-29
Windows is in a logical partition (number 5) filling the extended partition (number 1) at the start of the drive.

There is a primary partition (number 2) with 10.7 GB directly after the extended partition. fdisk says it is a linux partition but parted does not see any file system in it.

Then comes the swap partition (number 3) and an ext4 partition (number 4). I guess you have installed Ubuntu into partition number 4.

The partition table is complicated, and it makes it difficult to increase the size of the Ubuntu partition. If you want to add disk space to a partition, it must be adjacent. And the swap area is sitting adjacent to the Ubuntu partition and blocking such actions.

-o-

There are several solutions. In any case, they are risky, and you need to ***backup the whole drive*** (make a clone or an image of it) ***or at least backup all your personal files***.

One alternative is to make a complete backup copy of your Ubuntu system (with ***rsync*** or ***tar***) and wipe the partitions 2, 3 and 4. And create a new root partition for Ubuntu leaving some space at the very end of the drive for the swap partition. That way you can get around 24 GB for Ubuntu, which might be enough.

And after that you can copy back Ubuntu from the backup fix the UUIDs of the partitions or the references in /etc/fstab ..., and re-install the bootloader.

Another similar alternative is to shrink the logical partition with Windows, and then shrink the extended partition, to create more drive space that can be used for Ubuntu (to be merged with the space from partitions 2, 3 and 4).

*Edit*: Boot from the Ubuntu install CD/DVD/USB drive and use ***gparted*** to edit the partitions.

-o-

If you feel it is OK to re-install Ubuntu after releasing drive space, that would be the most straight-forward way to make a good system.

---

### Post by KraXarN on 2013-10-31
Thanks for the help. I tried doing some of those, but I just ended up reinstalling Ubuntu. Thanks anyway :)

---

