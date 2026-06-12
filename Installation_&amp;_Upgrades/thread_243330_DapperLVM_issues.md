---
title: "Dapper/LVM issues"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by Malibyte on 2006-08-24
Hi all -

I'm trying to set up MythTV on an Ubuntu 6.06 (Dapper) box with two SATA drives.  The partitions to be used for storing the video files are /dev/sda13 (approx. 250GB) and /dev/sdb1 (300GB).

Those partitions are set up as type 8e (Linux LVM).  I have tried fromatting them as ext3 and jfs with the same results.  The format goes fine, I can create the physical volumes with pvcreate, but then trying to create the volume group with vgcreate fails:

The first partition:
```

root@vader:/etc/default# pvcreate -vv /dev/sda13
File descriptor 3 left open
File descriptor 5 left open
File descriptor 7 left open
    Logging initialised at Thu Aug 24 17:43:25 2006

    Set umask to 0077
pvcreate      Setting global/locking_type to 1
pvcreate      Setting global/locking_dir to /var/lock/lvm
pvcreate      File-based locking enabled.
pvcreate      Locking /var/lock/lvm/P_orphans WB
pvcreate      /dev/sda13: No label detected
pvcreate      /dev/sda13: size is 515847087 sectors
pvcreate      metadata/pvmetadatasize not found in config: defaulting to 255
pvcreate      metadata/pvmetadatacopies not found in config: defaulting to 1
pvcreate      /dev/sda13: size is 515847087 sectors
pvcreate    Set up physical volume for "/dev/sda13" with 515846703 available sectors
pvcreate      Scanning for labels to wipe from /dev/sda13
pvcreate    Zeroing start of device /dev/sda13
pvcreate      Writing physical volume data to disk "/dev/sda13"
pvcreate      /dev/sda13: Writing label to sector 1
pvcreate  Physical volume "/dev/sda13" successfully created
pvcreate      Unlocking /var/lock/lvm/P_orphans
pvcreate    Wiping internal VG cache

```

So far, so good.  The second partition:

```

root@vader:/etc/default# pvcreate -vv /dev/sdb1
File descriptor 3 left open
File descriptor 5 left open
File descriptor 7 left open
    Logging initialised at Thu Aug 24 17:44:28 2006

    Set umask to 0077
pvcreate      Setting global/locking_type to 1
pvcreate      Setting global/locking_dir to /var/lock/lvm
pvcreate      File-based locking enabled.
pvcreate      Locking /var/lock/lvm/P_orphans WB
pvcreate      /dev/sdb1: No label detected
pvcreate      /dev/sdb1: size is 625137282 sectors
pvcreate      metadata/pvmetadatasize not found in config: defaulting to 255
pvcreate      metadata/pvmetadatacopies not found in config: defaulting to 1
pvcreate      /dev/sdb1: size is 625137282 sectors
pvcreate    Set up physical volume for "/dev/sdb1" with 625136898 available sectors
pvcreate      Scanning for labels to wipe from /dev/sdb1
pvcreate    Zeroing start of device /dev/sdb1
pvcreate      Writing physical volume data to disk "/dev/sdb1"
pvcreate      /dev/sdb1: Writing label to sector 1
pvcreate  Physical volume "/dev/sdb1" successfully created
pvcreate      Unlocking /var/lock/lvm/P_orphans
pvcreate    Wiping internal VG cache

```

Again, so far, so good.  Now:

```

root@vader:/etc/default# vgcreate -v myth_disks /dev/sda13 /dev/sdb1
File descriptor 3 left open
File descriptor 5 left open
File descriptor 7 left open
    Logging initialised at Thu Aug 24 17:46:03 2006

    Set umask to 0077
vgcreate    Wiping cache of LVM-capable devices
vgcreate    Adding physical volume '/dev/sda13' to volume group 'myth_disks'
vgcreate  No physical volume label read from /dev/sda13
vgcreate  /dev/sda13 not identified as an existing physical volume
vgcreate  Unable to add physical volume '/dev/sda13' to volume group 'myth_disks'.
vgcreate    Wiping internal VG cache

```

OK; pvcreate said both physical volumes were created, but vgcreate won't add the first volume.  The same thing happens if I simply give it /dev/sdb1 as the only volume to add.

Can anyone see what I'm doing wrong here? 

Thanks in advance --
Bob

---

### Post by mlind on 2006-08-24
Could you post the outputs of pvscan, pvdisplay, vgscan and vgdisplay.

---

### Post by Malibyte on 2006-08-25
Sure:

```

root@vader:/home/rcs# pvscan
File descriptor 4 left open
    Logging initialised at Thu Aug 24 20:55:25 2006

    Set umask to 0077
pvscan    Wiping cache of LVM-capable devices
pvscan    Wiping internal VG cache
pvscan    Walking through all physical volumes
pvscan  PV /dev/evms/sda13         lvm2 [245.97 GB]
pvscan  PV /dev/evms/sdb1          lvm2 [298.09 GB]
pvscan  Total: 2 [544.06 GB] / in use: 0 [0   ] / in no VG: 2 [544.06 GB]
pvscan    Wiping internal VG cache


```

```

root@vader:/home/rcs# pvdisplay
File descriptor 4 left open
    Logging initialised at Thu Aug 24 20:56:56 2006

    Set umask to 0077
pvdisplay    Scanning for physical volume names
pvdisplay    Wiping cache of LVM-capable devices
pvdisplay  --- NEW Physical volume ---
pvdisplay  PV Name               /dev/evms/sda13
pvdisplay  VG Name
pvdisplay  PV Size               245.97 GB
pvdisplay  Allocatable           NO
pvdisplay  PE Size (KByte)       0
pvdisplay  Total PE              0
pvdisplay  Free PE               0
pvdisplay  Allocated PE          0
pvdisplay  PV UUID               ovTzb3-iP63-Dg81-UJ7W-F9zC-xXSV-AExBzC
pvdisplay
pvdisplay  --- NEW Physical volume ---
pvdisplay  PV Name               /dev/evms/sdb1
pvdisplay  VG Name
pvdisplay  PV Size               298.09 GB
pvdisplay  Allocatable           NO
pvdisplay  PE Size (KByte)       0
pvdisplay  Total PE              0
pvdisplay  Free PE               0
pvdisplay  Allocated PE          0
pvdisplay  PV UUID               xrYOXP-SyKs-MFaE-nRKr-QsWx-bB0U-T9rHpq
pvdisplay
pvdisplay    Wiping internal VG cache


```

Since the volume group was never created, there's nothing here:

```

root@vader:/home/rcs# vgscan
File descriptor 4 left open
    Logging initialised at Thu Aug 24 20:58:58 2006

    Set umask to 0077
vgscan    Wiping cache of LVM-capable devices
vgscan    Wiping internal VG cache
vgscan  Reading all physical volumes.  This may take a while...
vgscan    Finding all volume groups
vgscan    Wiping internal VG cache


```

```

root@vader:/home/rcs# vgdisplay
File descriptor 4 left open
    Logging initialised at Thu Aug 24 21:00:09 2006

    Set umask to 0077
vgdisplay    Finding all volume groups
vgdisplay    Wiping internal VG cache


```

---

### Post by Malibyte on 2006-08-27
OK...I also have Mandriva 2006.0 x86_64 installed on the same box and tried it there...no problem; it created the volume group without a hitch.  Is there a config file I can move over and have it be usable in Ubuntu?

---

### Post by mlind on 2006-08-28
> **Malibyte said:**
> OK...I also have Mandriva 2006.0 x86_64 installed on the same box and tried it there...no problem; it created the volume group without a hitch.  Is there a config file I can move over and have it be usable in Ubuntu?

With Mandriva you got exact same commands to work? I think you should file bug report about this, IMO it's quite critical one if Dapper LVM tools can't perform the same..
LVM data is stored somewhere of the partition/disk/MBR/?, so Dapper should automatically just see current LVM state. Then you just need to create LV's, and finally partitions inside LV's.

---

### Post by Malibyte on 2006-08-28
Yep, got the whole thing configured under Mandriva...LV created and formatted, for a total of 544GB.  I'll be happy to file a bug report.  What's the URL?

---

### Post by mlind on 2006-08-28
[https://launchpad.net/distros/ubuntu/+source/lvm2/+bugs](https://launchpad.net/distros/ubuntu/+source/lvm2/+bugs)

---

### Post by Malibyte on 2006-08-28
Bug report submitted.

---

