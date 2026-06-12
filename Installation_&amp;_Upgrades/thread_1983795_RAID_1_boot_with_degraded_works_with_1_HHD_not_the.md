---
title: "RAID 1 boot with degraded works with 1 HHD not the other (grub-install already run)"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by bastienauneau on 2012-05-20
Hi

I have just made a fresh install of Ubuntu 12.04 following :
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

I've seen it's intended to 9.10, but I already succeed with these on 11.04 and 11.10 at work. I also installed grub on both HDD sda and sdb

cat /proc/mdstat shows correct data, HDD are in sync

When I boot from sda (turn off and remove sata cable from sdb hdd) the PC boots up and fine. When doing the other way around it does not manage to boot. I see the welcome screen of the bios ("press del to enter setup, etc..). Grub does NOT show up. Then it turns off and try booting again, etc...

I've tried to install grub again, it reports no error, but I can't still boot from sdb

To summarize :
_ boot ok witj sda and sdb
_ boot ok degraded with sda
_ does not boot degraded with sdb
_ I have run few times already (to be sure) :

bastien@mediaBox:~$ sudo grub-install /dev/sdb
[sudo] password for bastien: 
Installation finished. No error reported.
bastien@mediaBox:~$ 

Thanks

---

### Post by bastienauneau on 2012-05-21
I ran a fdsidk and found :
```

bastien@mediaBox:~$ sudo fdisk -l
[sudo] password for bastien: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000f1d70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     7813119     3905536   82  Linux swap / Solaris
/dev/sda2         7813120    85938175    39062528   fd  Linux RAID autodetect
/dev/sda3        85938176  1257814015   585937920   fd  Linux RAID autodetect
/dev/sda4      1257814016  1953523711   347854848   fd  Linux RAID autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00048298

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     7813119     3905536   82  Linux swap / Solaris
/dev/sdb2         7813120    85938175    39062528   fd  Linux RAID autodetect
/dev/sdb3        85938176  1257814015   585937920   fd  Linux RAID autodetect
/dev/sdb4      1257814016  1953523711   347854848   fd  Linux RAID autodetect

```

that the /dev/sdb1 (swap) was bootable
So I decided to re-init sdb as if it was a new spare HDD


```
bastien@mediaBox:~$ sudo mdadm --manage /dev/md0 --fail /dev/sdb2
mdadm: set /dev/sdb2 faulty in /dev/md0
bastien@mediaBox:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda3[0] sdb3[2]
      585936760 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 sda4[0] sdb4[2]
      347853688 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sda2[0] sdb2[2](F)
      39061432 blocks super 1.2 [2/1] [U_]
      
unused devices: <none>
bastien@mediaBox:~$ sudo mdadm --manage /dev/md1 --fail /dev/sdb3
mdadm: set /dev/sdb3 faulty in /dev/md1
bastien@mediaBox:~$ sudo mdadm --manage /dev/md2 --fail /dev/sdb4
mdadm: set /dev/sdb4 faulty in /dev/md2
bastien@mediaBox:~$ 
bastien@mediaBox:~$ 
bastien@mediaBox:~$ sudo mdadm --manage /dev/md0 --remove /dev/sdb2
mdadm: hot removed /dev/sdb2 from /dev/md0
bastien@mediaBox:~$ sudo mdadm --manage /dev/md1 --remove /dev/sdb3
mdadm: hot removed /dev/sdb3 from /dev/md1
bastien@mediaBox:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda3[0]
      585936760 blocks super 1.2 [2/1] [U_]
      
md2 : active raid1 sda4[0] sdb4[2](F)
      347853688 blocks super 1.2 [2/1] [U_]
      
md0 : active raid1 sda2[0]
      39061432 blocks super 1.2 [2/1] [U_]
      
unused devices: <none>
bastien@mediaBox:~$ sudo mdadm --manage /dev/md2 --remove /dev/sdb4
mdadm: hot removed /dev/sdb4 from /dev/md2
bastien@mediaBox:~$ 
bastien@mediaBox:~$ 
bastien@mediaBox:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda3[0]
      585936760 blocks super 1.2 [2/1] [U_]
      
md2 : active raid1 sda4[0]
      347853688 blocks super 1.2 [2/1] [U_]
      
md0 : active raid1 sda2[0]
      39061432 blocks super 1.2 [2/1] [U_]
      
```
//////////////: reboot the system ////////////////////:

```
root@mediaBox:~# sfdisk -d /dev/sda | sfdisk --no-reread /dev/sdb

Disk /dev/sdb: 121601 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+    486-    487-   3905536   82  Linux swap / Solaris
/dev/sdb2        486+   5349-   4864-  39062528   fd  Linux RAID autodetect
/dev/sdb3       5349+  78295-  72946- 585937920   fd  Linux RAID autodetect
/dev/sdb4      78295+ 121601-  43306- 347854848   fd  Linux RAID autodetect
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1          2048   7813119    7811072  82  Linux swap / Solaris
/dev/sdb2       7813120  85938175   78125056  fd  Linux RAID autodetect
/dev/sdb3      85938176 1257814015 1171875840  fd  Linux RAID autodetect
/dev/sdb4     1257814016 1953523711  695709696  fd  Linux RAID autodetect
Warning: partition 1 does not end at a cylinder boundary
Warning: partition 2 does not start at a cylinder boundary
Warning: partition 2 does not end at a cylinder boundary
Warning: partition 3 does not start at a cylinder boundary
Warning: partition 3 does not end at a cylinder boundary
Warning: partition 4 does not start at a cylinder boundary
Warning: partition 4 does not end at a cylinder boundary
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed.
Run partprobe(8), kpartx(8) or reboot your system now,
before using mkfs
If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
root@mediaBox:~# 
root@mediaBox:~# 
root@mediaBox:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000f1d70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     7813119     3905536   82  Linux swap / Solaris
/dev/sda2         7813120    85938175    39062528   fd  Linux RAID autodetect
/dev/sda3        85938176  1257814015   585937920   fd  Linux RAID autodetect
/dev/sda4      1257814016  1953523711   347854848   fd  Linux RAID autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00048298

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     7813119     3905536   82  Linux swap / Solaris
/dev/sdb2         7813120    85938175    39062528   fd  Linux RAID autodetect
/dev/sdb3        85938176  1257814015   585937920   fd  Linux RAID autodetect
/dev/sdb4      1257814016  1953523711   347854848   fd  Linux RAID autodetect

Disk /dev/md1: 600.0 GB, 599999242240 bytes
2 heads, 4 sectors/track, 146484190 cylinders, total 1171873520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 356.2 GB, 356202176512 bytes
2 heads, 4 sectors/track, 86963422 cylinders, total 695707376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md0: 40.0 GB, 39998906368 bytes
2 heads, 4 sectors/track, 9765358 cylinders, total 78122864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
root@mediaBox:~# 
root@mediaBox:~# 
root@mediaBox:~# 
root@mediaBox:~# mdadm --manage /dev/md
md/  md0  md1  md2  
root@mediaBox:~# mdadm --manage /dev/md0 /dev/sdb
sdb   sdb1  sdb2  sdb3  sdb4  
root@mediaBox:~# mdadm --manage /dev/md0 --add /dev/sdb2
mdadm: /dev/sdb2 reports being an active member for /dev/md0, but a --re-add fails.
mdadm: not performing --add as that would convert /dev/sdb2 in to a spare.
mdadm: To make this a spare, use "mdadm --zero-superblock /dev/sdb2" first.
root@mediaBox:~# mdadm --zero-superblock /dev/sdb2
root@mediaBox:~# mdadm --manage /dev/md0 --add /dev/sdb2
mdadm: added /dev/sdb2
root@mediaBox:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb2[2] sda2[0]
      39061432 blocks super 1.2 [2/1] [U_]
      [>....................]  recovery =  1.9% (780032/39061432) finish=6.5min speed=97504K/sec
      
md2 : active raid1 sda4[0]
      347853688 blocks super 1.2 [2/1] [U_]
      
md1 : active raid1 sda3[0]
      585936760 blocks super 1.2 [2/1] [U_]

```

This was a bit overkill to remove a boot flag, but I wanted to be sure it get fixed !
So the flag is away now, and both HDD are strictly identical :

```
bastien@mediaBox:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sda4[0] sdb4[2]
      347853688 blocks super 1.2 [2/2] [UU]
      
md1 : active raid1 sda3[0] sdb3[2]
      585936760 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sda2[0] sdb2[2]
      39061432 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
bastien@mediaBox:~$ sudo fdisk -l
[sudo] password for bastien: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000f1d70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     7813119     3905536   82  Linux swap / Solaris
/dev/sda2         7813120    85938175    39062528   fd  Linux RAID autodetect
/dev/sda3        85938176  1257814015   585937920   fd  Linux RAID autodetect
/dev/sda4      1257814016  1953523711   347854848   fd  Linux RAID autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00048298

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     7813119     3905536   82  Linux swap / Solaris
/dev/sdb2         7813120    85938175    39062528   fd  Linux RAID autodetect
/dev/sdb3        85938176  1257814015   585937920   fd  Linux RAID autodetect
/dev/sdb4      1257814016  1953523711   347854848   fd  Linux RAID autodetect

Disk /dev/md0: 40.0 GB, 39998906368 bytes
2 heads, 4 sectors/track, 9765358 cylinders, total 78122864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 600.0 GB, 599999242240 bytes
2 heads, 4 sectors/track, 146484190 cylinders, total 1171873520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 356.2 GB, 356202176512 bytes
2 heads, 4 sectors/track, 86963422 cylinders, total 695707376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table
```

But I still have the same problem, it boots if only sda is present, not when only sdb
Swapping HDD from sda/sdb does not help. It's alwyas the same HDD that refuses to boot alone. Both together work fine

---

### Post by bastienauneau on 2012-05-21
I've changed mdadm.conf into :

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers
DEVICE /dev/sda* /dev/sdb*

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR bastienauneau@gmail.com

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=822421da:5e8ffe2e:3bd7c269:4a64d0d9 name=mediaBox:0
ARRAY /dev/md/1 metadata=1.2 UUID=ccb369f8:a55bb5e1:918bb805:00efa2b3 name=mediaBox:1
ARRAY /dev/md/2 metadata=1.2 UUID=7fb59208:3698f6ca:ee292d6c:b90455f9 name=mediaBox:2

```

I've added the line :
DEVICE /dev/sda* /dev/sdb*
but it did not help...

I'm running out of idea
It seems that when only /dev/sdb is pugged, the system does not boot, as they are no log created in /var/log/kern.log
I've ran thousand of times sudo grub-install /dev/sdb but this does not help

---

### Post by darkod on 2012-05-21
What do you have in /etc/fstab? Can it be that sda1 is specified as swap and when the disk is missing it's stopping the boot because of that?

Although in theory it should allow you to skip looking for swap with 'S'.

That's the only thing on my mind seeing that swap is not on the array.

Also, you don't need to create so many different md devices, you can have one with different partitions of course.

I would double check how is swap defined in fstab, other than that I'm also stumped...

EDIT PS: You can also run the boot info script with both disks connected and see the results.

---

### Post by bastienauneau on 2012-05-21
fstab file :
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=a79ed33c-6fe4-44c8-8335-562f5acf313d /               ext4    errors=remount-ro 0       1
# /backup_partition was on /dev/md2 during installation
UUID=af06ab43-3a1d-48d6-a8b0-f78f8be9ddbd /backup_partition ext4    defaults        0       2
# /home was on /dev/md1 during installation
UUID=9c939416-2f0b-46db-a1e5-0ef6bf6b3115 /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=b73dd5ea-bf20-4907-a681-b6edeecaa32c none            swap    sw              0       0
# swap was on /dev/sdb1 during installation
UUID=1735fe87-37b5-4d88-8e5b-fb7ada556883 none            swap    sw              0       0
```

swap is already inside
Should I set any boot flag ? there's no boot flag on sda2, but it boots. Should I try setting boot flag on sdb2, or this would break the raid ?

system partion is md0 based on sda2 and sdb2
system boot ok with both HDD, or only sda
system does not boot with only sdb
swapping both HDD sata cable does not help

Content of RESULT.txt from boot info script


```
bastien@mediaBox:~/bootinfoscript-061$ cat RESULTS.txt 
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/822421da5e8ffe2e3bd7c2694a64d0d9)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/822421da5e8ffe2e3bd7c2694a64d0d9)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb4: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

md/0: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /dev/md0 already mounted or MDRaid/md/0 busy
mount: according to mtab, /dev/md0 is mounted on /

md/1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /dev/md0 already mounted or MDRaid/md/0 busy
mount: according to mtab, /dev/md0 is mounted on /
mount: /dev/md1 already mounted or MDRaid/md/1 busy
mount: according to mtab, /dev/md1 is mounted on /home

md/2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /dev/md0 already mounted or MDRaid/md/0 busy
mount: according to mtab, /dev/md0 is mounted on /
mount: /dev/md1 already mounted or MDRaid/md/1 busy
mount: according to mtab, /dev/md1 is mounted on /home
mount: /dev/md2 already mounted or MDRaid/md/2 busy
mount: according to mtab, /dev/md2 is mounted on /backup_partition

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               4,096     7,813,119     7,809,024  82 Linux swap / Solaris
/dev/sda2           7,813,120    85,938,175    78,125,056  fd Linux raid autodetect
/dev/sda3          85,938,176 1,257,814,015 1,171,875,840  fd Linux raid autodetect
/dev/sda4       1,257,814,016 1,953,523,711   695,709,696  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               4,096     7,813,119     7,809,024  82 Linux swap / Solaris
/dev/sdb2           7,813,120    85,938,175    78,125,056  fd Linux raid autodetect
/dev/sdb3          85,938,176 1,257,814,015 1,171,875,840  fd Linux raid autodetect
/dev/sdb4       1,257,814,016 1,953,523,711   695,709,696  fd Linux raid autodetect


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/md0         a79ed33c-6fe4-44c8-8335-562f5acf313d   ext4       
/dev/md1         9c939416-2f0b-46db-a1e5-0ef6bf6b3115   ext4       
/dev/md2         af06ab43-3a1d-48d6-a8b0-f78f8be9ddbd   ext4       
/dev/sda1        b73dd5ea-bf20-4907-a681-b6edeecaa32c   swap       
/dev/sda2        822421da-5e8f-fe2e-3bd7-c2694a64d0d9   linux_raid_member mediaBox:0
/dev/sda3        ccb369f8-a55b-b5e1-918b-b80500efa2b3   linux_raid_member mediaBox:1
/dev/sda4        7fb59208-3698-f6ca-ee29-2d6cb90455f9   linux_raid_member mediaBox:2
/dev/sdb1        1735fe87-37b5-4d88-8e5b-fb7ada556883   swap       
/dev/sdb2        822421da-5e8f-fe2e-3bd7-c2694a64d0d9   linux_raid_member mediaBox:0
/dev/sdb3        ccb369f8-a55b-b5e1-918b-b80500efa2b3   linux_raid_member mediaBox:1
/dev/sdb4        7fb59208-3698-f6ca-ee29-2d6cb90455f9   linux_raid_member mediaBox:2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/md0         /                        ext4       (rw,errors=remount-ro)
/dev/md1         /home                    ext4       (rw)
/dev/md2         /backup_partition        ext4       (rw)


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

bastien@mediaBox:~/bootinfoscript-061$ 

```

---

### Post by darkod on 2012-05-21
1. The boot flag is not used on linux, so you don't need it anywhere. However, sometimes some boards don't boot at all if they don't detect a boot flag on any partition.

2. Here is your issue:
Look at the top of the results, grub2 is looking for the partition with UUID ending with 'd0d9'. Both grub2 from both disks are searching for this UUID.

But that UUID is not of the /dev/md0, instead it's from /dev/sda2. That's why it doesn't boot without /dev/sda.

Grub2 somehow needs to search for the /dev/md0 with UUID ending in '313d'.

Try this from live mode, but without any partitions mounted. I see when the script was running it reports some md devices as mounted, don't know if you mounted them before running it.

So, without mounting anything, in live mode try this:
sudo mount /dev/md0 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --root-directory=/mnt /dev/sdb

Restart first with both disks and see if it worked. Then restart with only /dev/sda. Then connect /dev/sdb first and let it sync so that it doesn't lose touch with /dev/sda.
Only after everything is synced, try with only /dev/sdb in the system.

RAID1 can sometimes be messed up if you disconnect one of the disk, and then without letting them sync disconnect the other immediately.

---

### Post by darkod on 2012-05-21
Sorry, my mistake. Live mode doesn't recognize md devices by default. Slipped my mind.

First install the mdadm package and assemble the devices:
sudo apt-get install mdadm
sudo mdadm --assemble --scan

That should auto assemble it. Check if they are OK with the:
cat /proc/mdstat

If everything is fine, proceed with installing grub2 as above.

PS. Also it's better to remove the line you added to mdadm.conf. Leave the default line for DEVICES...

---

### Post by bastienauneau on 2012-05-21
But I thought that at the time of boot, mdadm is not active yet, so it boots from disk as if it were a normal partition, then after starts mdadm

Also the UUID is the same for sda2 and sdb2, is this a problem ?

---

### Post by darkod on 2012-05-21
Oops, never saw that...

Hm, in that case it looks fine. Let me think a little. :)

---

### Post by darkod on 2012-05-21
Looks like my thinking hat is broken. Or on strike. :)

Let me call some help from a better raid expert.

---

### Post by rubylaser on 2012-05-21
Here's a silly question before I look into this any further.  Do you have /dev/sdb setup in the BIOS as a bootable device and have the BIOS setup to boot alternate in case the first boot device is not available?

Also, with all of the changes you've done, I assume you've set the boot degraded option, because it's booting missing one disk, but you might try updating your initramfs again.
```

sudo update-initramfs -k all -u

```

Otherwise, I'll have to give this a try in Virtualbox, because to my eye, this looks to be correct (although, it's been a long day :) )

---

### Post by bastienauneau on 2012-05-23
Youhou !! It works !!
Sorry for the late answer, but it was sunny and warm outside, so ... not much time for the computer :)

The sudo update-initramfs -k all -u did the trick
I have also played around with some boot order options in the bios, but I don't think it changed anything.

According to [http://man.he.net/man8/update-initramfs](http://man.he.net/man8/update-initramfs)
the ramfs is used at boot time to init what is loaded in ram, then it is used as initial root system. What do you think was missing in my ramfs ? The mdadm module ? something related to grub entries ? If you have some more inputs, I'd like to learn more about what really happen in my setup

Thanks again anyway !!

---

### Post by darkod on 2012-05-23
I told you, an expert is an expert. :)

Glad you (he) solved it.

---

### Post by ikcalb on 2012-08-22
Opened own thread (this one is already solved :s)
[http://ubuntuforums.org/showthread.php?p=12188689#post12188689](http://ubuntuforums.org/showthread.php?p=12188689#post12188689)

[quote=ikcalb]
Hello!

I'm running
> "Debian squeeze 6.0.5" (stable)
> Linux server 2.6.32-5-amd64
on my Fujitsu ESPRIMO P5915 homeserver.


I do have almost the same problem as the threadstarter:

/              on /dev/md0  (raid10f2)
swap        on /dev/md5  (raid10f2) - thaught of changing to non-raid
/home      on /dev/md6  (raid10f2)
/backup    on /dev/md3  (raid10f2, mounted --noauto, just when executing backups)

My machine is able to boot from (chosen via bios boot-menu)
- any hd (if both are present)
- sda, degraded

But NOT bootable from sdb degraded.


The solution of @rubylaser didn't work for me.
Any suggestion welcom!

Best regards, Florian

P.S.: partition layouts are identical, mdstat & fstab configured:

P.P.S.: Excuse my English
[/quote]

---

### Post by vktRus on 2013-04-03
Shortly put: adding the 'GRUB_TERMINAL=console' to  '/etc/default/grub' (and executing 'update-grub' afterwards) allows to  circumvent the issue (verified on Ubuntu/Quantal 12.10).
[bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1073108")

---

