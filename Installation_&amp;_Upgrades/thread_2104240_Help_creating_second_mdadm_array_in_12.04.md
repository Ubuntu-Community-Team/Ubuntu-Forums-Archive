---
title: "Help creating second mdadm array in 12.04"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by ltburch2000 on 2013-01-12
I have an existing mdadm array on my server

I have added 4 more drives and am trying to create a second raid 6 array.

This should be quite simple, the command is

sudo mdadm --create /dev/md1 ––level=6 ––raid-devices=4 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1

The drives all have partition tables and the partitions have been created but unformatted (these are 3 TB drives/partitions if it matters).

However when I go to create the array I get the error:

mdadm: no raid-devices specified.

I can't figure it out, this should be very simple but it simply does not work.

---

### Post by darkod on 2013-01-12
Are the partitions created of raid type (code fd I think)? Or they are simple linux partitions code 82.

They need to be raid type, have the raid flag set in parted for example. You can do it easily in parted with:
sudo parted /dev/sde
set 1 raid on
quit

For all disks. After that tyr the mdadm --create again.

---

### Post by ltburch2000 on 2013-01-12
I tried setting the raid flag on all the partitions.  Same result.

I have not found any mention of this flag beeing needed my mdadm, but I tried it anyway.

Is it mdadm saying it can't find the devices to make the raid array?  Is there some kind of test I can run to display the drive details?  Is there an alternate way to specify the devices like uuid?

---

### Post by darkod on 2013-01-12
Of course it needs the raid flag in parted, or the fd type in fdisk/cfdisk. That labels the partition as linux software raid device.

After that, formatting with a filesystem is done on the mdX device, not on the partitions.

Look at all your disks, you will probably see the existing array partitions marked like that too:
sudo parted -l (small L)

Post the output of that command. You can also post:
sudo fdisk -l

As far as I know, you used the correct command.

---

### Post by ltburch2000 on 2013-01-12
the volumes I am trying to get into the array are the 3TB volumes.

parted -l 

Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sde: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB                     raid


Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sdf: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB                     raid


Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sdg: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB                     raid


Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sdh: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB                     raid


Model: ATA WDC WD10EVVS-73M (scsi)
Disk /dev/sdi: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  xfs


Model: ATA WDC WD20EARX-00P (scsi)
Disk /dev/sdj: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary


Model: ATA ST31000528AS (scsi)
Disk /dev/sdl: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1048kB  734GB  734GB   extended                  boot
 5      1049kB  734GB  734GB   logical   ext4
 2      734GB   742GB  8193MB  primary   linux-swap(v1)


Model: ATA WDC WD20EARX-00P (scsi)
Disk /dev/sdm: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary


Model: ATA WDC WD20EARX-00P (scsi)
Disk /dev/sdk: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary


Model: Linux Software RAID Array (md)
Disk /dev/md0: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  4001GB  4001GB  ext4


fdisk -l


Disk /dev/sde: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdf: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdg: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdh: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ef74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1            2048  1953523711   976760832   83  Linux

Disk /dev/sdj: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000813e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1            2048  3907028991  1953513472   83  Linux

Disk /dev/sdl: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000506e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1   *        2046  1433591807   716794881    5  Extended
/dev/sdl2      1433591808  1449592831     8000512   82  Linux swap / Solaris
/dev/sdl5            2048  1433591807   716794880   83  Linux

Disk /dev/sdm: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000197ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1            2048  3907028991  1953513472   83  Linux

Disk /dev/sdk: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d3c64

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1            2048  3907028991  1953513472   83  Linux

Disk /dev/md0: 4000.8 GB, 4000792444928 bytes
2 heads, 4 sectors/track, 976755968 cylinders, total 7814047744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

---

### Post by darkod on 2013-01-12
Few google hits mention that error message in relation with the --raid-devices option. In your first post you had the mdadm command right except that in front of level and raid-devices you have one long hyphen instead of two short ones. I thought it's only a formatting error so didn't pay much attention. You are typing the command correctly right? Like:
```
sudo mdadm --create /dev/md1 --level=6 --raid-devices=4 ....
```

Otherwise it all looks good and I really can't see a reason. Unless using 3TB drives is the reason but I think it supports much bigger arrays/disks.

---

### Post by ltburch2000 on 2013-01-12
The conversion to one long dash from two smaller ones must be from the editor.  I do have two dashes for the command.

---

### Post by darkod on 2013-01-13
In that case I don't have a clue, sorry.

You can try writing a blank gpt table on these four disks and create the raid partitions again, but this is more a desperate attempt, I don't see anything really wrong with them. You can use parted or Gparted depending what is better for you. With Gparted don't forget to create the partition as raid type right away, I wonder if this is the current issue if they were created as "normal" linux partition so it is not recognizing them as raid devices even with the raid flag that was added later. The thing is that if they were raid type from the start, the raid flag should have been there already. If Gparted doesn't have option for raid type (I don't remember right now), use parted.
In parted after creating the partition set the raid flag on right away.

As I said, this is more of a desperate attempt, I don't see much wrong in how you did it.

---

### Post by rubylaser on 2013-01-13
> **darkod said:**
> Of course it needs the raid flag in parted, or the fd type in fdisk/cfdisk. That labels the partition as linux software raid device.

After that, formatting with a filesystem is done on the mdX device, not on the partitions.

Look at all your disks, you will probably see the existing array partitions marked like that too:
sudo parted -l (small L)

Post the output of that command. You can also post:
sudo fdisk -l

As far as I know, you used the correct command.

darkod, thanks for your help with mdadm:) But ,it is not necessary to pass the fd flag to non-bootable partitions anymore.  It can make your disks easier to identify as raid members, but mdam will happily use disks with the 83 (Linux) flag to create an array.

Also, I got a PM from ltburch2000 that he was able to figure it out by one of my previous posts.  I've asked him to send me the link if he has a chance, so we can update this thread to include the solution.

---

### Post by darkod on 2013-01-13
> **rubylaser said:**
> darkod, thanks for your help with mdadm:) But ,it is not necessary to pass the fd flag to non-bootable partitions anymore.  It can make your disks easier to identify as raid members, but mdam will happily use disks with the 83 (Linux) flag to create an array.

Also, I got a PM from ltburch2000 that he was able to figure it out by one of my previous posts.  I've asked him to send me the link if he has a chance, so we can update this thread to include the solution.

OK, didn't know that. I thought the partitin type is necessary so that mdadm can accept the partition as physical device. Thanks.

---

