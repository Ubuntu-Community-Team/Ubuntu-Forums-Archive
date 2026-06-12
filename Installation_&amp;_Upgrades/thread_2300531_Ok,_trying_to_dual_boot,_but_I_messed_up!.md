---
title: "Ok, trying to dual boot, but I messed up!"
date: 2015-10-26
forum: Installation &amp; Upgrades
---

### Post by theparrotsketch on 2015-10-26
Hi there, trying to get a laptop to dual boot, I was going through the Ubuntu installation option of something else- but couldn't resize the partition to let me continue. So I clicked use logical volume management but didn't go further than the next stage, it just created a logical volume and extended volume. This didn't look right either, so I quit before really messing up! Now, of course, I cannot boot into windows to back up before committing to writing to the whole drive.
  Have I now lost all windows data? I didn't want to delete either logical or extended partitions for fear of losing data. But I cannot mount either to see where the data is!( 
Any help would be awesome!

---

### Post by anjo_ed on 2015-10-26
So, Did you try to boot windows ? I think that you did not apply the new setting, right ?

---

### Post by theparrotsketch on 2015-10-26
Thanks, I've lost the partitioning system and most likely the boot for windows. So I haven't been able to get back into it or even get that partition to mount so I can get to the files:( I'm just hoping I can recover them as I haven't formatted anything that I know of!

---

### Post by yancek on 2015-10-26
If you had windows previously installed on the computer, you should have used the Disk Management tool in windows to resize/shrink the windows partition.  After doing that, you should reboot and run chkdsk at least once to verify that everything still works.  You should then have unallocated space on the disk on which to install another OS (Ubuntu).  

Backing up data should be done before you start changing partitions or installing a new OS.
You selected the LVM option which as I understand it, overwrites everything although I don't know if that would have happened at the stage your were at?  
Which version of windows do you have?  If it is 8 or 10 it is hibernated and you will not be able to mount any ntfs partitions from Ubuntu.  
Boot the Ubuntu install medium and run the two commands below, post the output here:

```
sudo fdisk -l
sudo parted -l
```

That's a Lower Case Letter L in the commands.

---

### Post by theparrotsketch on 2015-10-26
Thanks yancek, you're right, I should have backed up from Ubuntu live when I had the chance;( Windows has been playing up and wouldn't load users, but I could still get to files using a live usb. It's windows xp, hence the need to set up something better! Neither the install or gparted gave me any option to shrink the volume so I backed out, but the install had already partitioned the drive.

sudo fdisk -l gives me

it@it:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d9d23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      499711      248832   83  Linux
/dev/sda2   *      501758   976771071   488134657    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 15.6 GB, 15631122432 bytes
255 heads, 63 sectors/track, 1900 cylinders, total 30529536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    30529535    15264752    c  W95 FAT32 (LBA)
it@it:~$ 


and sudo parted -l gives 

Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  256MB  255MB  primary
 2      257MB   500GB  500GB  primary               boot


Model: SanDisk 
Disk /dev/sdb: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  15.6GB  15.6GB  primary  fat32        boot, lba



I fear I may have made matters worse by telling disc to consider the partition ntfs, which just made one large un-mounted partition.
I have this sinking feeling 

If there is any way out of this mess I'll be gobsmacked, so I do appreciate your help!

---

