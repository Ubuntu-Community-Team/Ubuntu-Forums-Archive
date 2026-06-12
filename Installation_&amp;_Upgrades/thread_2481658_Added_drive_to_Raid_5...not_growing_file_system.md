---
title: "Added drive to Raid 5...not growing file system"
date: 2022-12-05
forum: Installation &amp; Upgrades
---

### Post by sftech13 on 2022-12-05
So I have 4, 6TB drives running RAID 5 no issues. I added another drive so now 5 drives for /home partition but it's not expanding the space. I looked at parted after mdadm grow and see the filesystem type is unknown (should be ext4) and partition table is unknown and I can't grow the file system.

What am I missing???

```

sftech13@ubuntu:~$ sudo parted /dev/md0
[sudo] password for sftech13:
GNU Parted 3.2
Using /dev/md0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit TB
(parted) print
Error: /dev/md0: unrecognised disk label
Model: Linux Software RAID Array (md)
Disk /dev/md0: 24.0TB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags:
(parted) quit
sftech13@ubuntu:~$ sudo parted -l
Model: ATA Samsung SSD 860 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  512MB   511MB   fat32                 boot, esp
 2      512MB   16.5GB  16.0GB  linux-swap(v1)
 3      16.5GB  66.5GB  50.0GB  ext4


Model: ATA ST6000VN0033-2EF (scsi)
Disk /dev/sdb: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  6001GB  6001GB


Model: ATA ST6000VN0033-2EE (scsi)
Disk /dev/sdc: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  6001GB  6001GB                     raid


Model: ATA ST6000VN0033-2EE (scsi)
Disk /dev/sdd: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  6001GB  6001GB                     raid


Model: ATA ST6000VN0033-2EE (scsi)
Disk /dev/sde: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  6001GB  6001GB                     raid


Model: ATA ST6000NE000-2KR1 (scsi)
Disk /dev/sdf: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  6001GB  6001GB


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg-home: 18.0TB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags:

Number  Start  End     Size    File system  Flags
 1      0.00B  18.0TB  18.0TB  ext4


Error: /dev/md0: unrecognised disk label
Model: Linux Software RAID Array (md)
Disk /dev/md0: 24.0TB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags:

```

---

### Post by TheFu on 2022-12-05
If you just add another device, then it will be used as the 2nd replacement device if there is a failure. BTW, I hope you setup the partitions correctly first too.  Never put RAID directly on whole disks, always, always, use partitions as RAID devices. There are many reasons, most of which matter when a drive fails.

---

### Post by sftech13 on 2022-12-06
I'm sorry if I didn't explain properly. I have RAID 5 on /Home partition and a small SSD for the other OS partitions. I had 4, 6TB drives then added a 5th to /dev/md0 to get 24TB with 1 spare but I cant expand the filesystem size to grow the size of 24TB, its staying at 16TB.

I dont understand or see where the additional drive I just added went to or how to increase the filesystem size.


Here is print out of md0 file system size
```
sftech13@ubuntu:~$ lsblk /dev/md0 -o size SIZE
21.9T
16.4T

```

Here is the print out of /Home
```
sftech13@ubuntu:~$ df -hT /homeFilesystem          Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg-home ext4   17T   13T  3.3T  80% /home



```


Here is the print out of pvdisplay
```
sftech13@ubuntu:~$ sudo pvdisplay  --- Physical volume ---
  PV Name               /dev/md0
  VG Name               vg
  PV Size               16.37 TiB / not usable 3.50 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              4292277
  Free PE               0
  Allocated PE          4292277
  PV UUID               JOZbKu-O4Kc-JQFF-aUAX-dlw9-n8VU-6lq1wB

```


Here is a print out of when I try to resize the LVM vgdisplay
```
sftech13@ubuntu:~$ sudo vgdisplay  --- Volume group ---
  VG Name               vg
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  6
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               16.37 TiB
  PE Size               4.00 MiB
  Total PE              4292277
  Alloc PE / Size       4292277 / 16.37 TiB
  Free  PE / Size       0 / 0
  VG UUID               TFn0Cz-m5cS-v4wK-tjv3-N9R3-ilWc-QSAS1e

```

Here is the print out of when I try to resize the system
```
sftech13@ubuntu:~$ sudo resize2fs /dev/md0resize2fs 1.44.1 (24-Mar-2018)
resize2fs: Device or resource busy while trying to open /dev/md0
Couldn't find valid filesystem superblock.



```


Here is the print out of mdadm --detail
```
sftech13@ubuntu:~$ sudo mdadm --detail /dev/md0/dev/md0:
           Version : 1.2
     Creation Time : Fri Jul  2 08:02:08 2021
        Raid Level : raid5
        Array Size : 23441561600 (22355.62 GiB 24004.16 GB)
     Used Dev Size : 5860390400 (5588.90 GiB 6001.04 GB)
      Raid Devices : 5
     Total Devices : 5
       Persistence : Superblock is persistent


     Intent Bitmap : Internal


       Update Time : Tue Dec  6 11:55:41 2022
             State : clean
    Active Devices : 5
   Working Devices : 5
    Failed Devices : 0
     Spare Devices : 0


            Layout : left-symmetric
        Chunk Size : 512K


Consistency Policy : bitmap


              Name : ubuntu:0  (local to host ubuntu)
              UUID : 6692ae2f:84dbdd67:3fba506d:213996b2
            Events : 147627


    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       49        1      active sync   /dev/sdd1
       2       8       33        2      active sync   /dev/sdc1
       3       8       81        3      active sync   /dev/sdf1
       4       8       17        4      active sync   /dev/sdb1

```

---

### Post by TheFu on 2022-12-06
If it were me, I'd ensure my backups were excellent. 
[https://raid.wiki.kernel.org/index.php/Growing#Extending_an_existing_RAID_array](https://raid.wiki.kernel.org/index.php/Growing#Extending_an_existing_RAID_array) is the best guide I found.
They warn this will take hours or days.

If it were me, I'd triple check my backups, wipe the array, and start over fresh with a new array, then restore the data from those backups.  If anything happens during the migration, you'll need to do that anyway.

---

### Post by sftech13 on 2022-12-06
Suggestions on how to back up 13TB of data? Just in case...

---

### Post by TheFu on 2022-12-06
> **sftech13 said:**
> Suggestions on how to back up 13TB of data? Just in case...

You don't have backups, but you have RAID?  Dude, you are doing this all wrong.
Backups address 1001 issues.
RAID solves 2 .... yes, 2 issues.

Ok, 

step 1. buy a 14+TB HDD.

step 2. create a partition (or better, multiple partitions sized to be no larger than your smallest backup disk you'll ever own) on the 14+TB HDD.  I don't allow any file systems to be larger than a 4TB partition can hold, so that's about 3.65TB.

step 3. Use 'rsync' as root to make a copy of everything for this single time.  It would be smart to use a better backup too that supports versioning in the future. I use 'rdiff-backup', but there are lots of tools.  rdiff-backup commands look very much like rsync commands because it uses librsync.  Most Unix backup tools use librsync.

step 4.  Validate that the files are all there with the correct owner, group, permissions, xattrs and ACLs.  Having just the data, isn't sufficient when it is time to restore, unless all the files have a single owner, which seems crazy to me.  Part of the validation is to count the number of directories, the number of files, and the total space used. Compare those numbers to the source.  Counts can be gathered using 'find' and 'wc'.  Storage used is a question for 'du' and 'df'

Of course, you can buy 4x4TB HDDs too, if you prefer.  I've bought used enterprise 4TB "Gold" drives for less than $50 each.  Unfortunately, of those drives, 50% had to be returned due to bad sectors. Any flaw seen on receipt is cause to get a replacement immediately.  OTOH, the remaining and replacement drives have been performing perfectly about 18 months. No new issues. Just the power-on-hours increasing.  These devices had 5 yr warranties when new. IME, I've never seen one fail before 10 yrs of use.  They came with a 2 yr "used" warranty from the seller.  I expect that seller has disappeared already. ;(  But if the drives continue, they will have been a bargain.  A few weeks ago, I picked up a new WD-Black 8TB HDD for $140. You could get 2 of those. They have 5 yr warranties and are performing great. "WD-Black" drives are the top performance drive for consumers - anyone outside a data center. They've always impressed me - 2.5 or 3.5inch versions. None have failed me. None, which is sorta surprising.  I've had Green, Blue, external USB, and the equivalent from every other vendor fail, but not the WD-Black line.

```
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Black
Device Model:     WDC WD1001FALS-00J7B0
...
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
...
  9 Power_On_Hours          0x0032   001   001   000    Old_age   Always       -       110042
...
```
Let's do the math ... That's 12.56 years.
And the new drive:
```

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD8002FZWX-00BKUA0
...
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       223

```
223 hours.  Oddly, all the other values say "Pre-fail" or "Old_age"  .... for a new HDD.  Even with ZERO power-on-hours, they claim "Pre-fail" and "Old_age" in the SMART data.

Anyway, probably more than you care to consider.

---

### Post by sftech13 on 2022-12-09
Sounds like I'm ordering a external drive. Thanks for the support. 

I have Seagate NAS 6TB 7200RPM drives. I will keep my eyes out for a new deal like you mentioned.

Thanks again

---

### Post by TheFu on 2022-12-09
Be very careful selecting drives.  

For individuals, it is hard to know where the statistics truly are, but there is an internet backup service that tracks drives and drive failures using the same models of HDDs that you and I might buy.  I'd encourage you to find that information, review some of their quarterly data, specifically as they were using the size HDD you plan to buy, to see which vendors and models perform significantly worse than others.  There are a few models that perform better, even much better, than others.  Is saving $20 really less expensive if the HDDs fail after 4 yrs when you could find a proven, better engineered model, that is likely to last twice as long?  

"RAID never replaces the need for backups." Always remember that.  Heck, google that statement to see what others say about it.

---

