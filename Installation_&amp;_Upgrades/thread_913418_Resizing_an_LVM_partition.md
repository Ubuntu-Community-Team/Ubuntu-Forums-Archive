---
title: "Resizing an LVM partition"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by jvincent08 on 2008-09-07
Alright, I've been googling all day on how to do this. All I wanted to do is shrink an LVM logical volume to free up some space. I've discovered that I need to first shrink the partition that is on the volume, so as not to lose data. The logical volume is spread across 2 320GB hard drives. Here's some info:
```

root@ubuntu:~# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d87b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    f  W95 Ext'd (LBA)
/dev/sda5               1       38913   312568609+  8e  Linux LVM

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000425a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      248976   83  Linux
/dev/sdb2              32         274     1951897+  82  Linux swap / Solaris
/dev/sdb3             275       38913   310367767+   5  Extended
/dev/sdb5             275       38913   310367736   8e  Linux LVM

root@ubuntu:~# lvdisplay
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver 
  --- Logical volume ---
  LV Name                /dev/VolGroup/Root
  VG Name                VolGroup
  LV UUID                YC6zl7-Wp92-U3s6-5fSE-6cbi-glYB-5qkLxe
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                30.00 GB
  Current LE             7680
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
   
  --- Logical volume ---
  LV Name                /dev/VolGroup/Home
  VG Name                VolGroup
  LV UUID                etLIAF-eok9-x4P6-5Rgp-X96r-qv8q-y59PLL
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                564.07 GB
  Current LE             144403
  Segments               2
  Allocation             inherit
  Read ahead sectors     0
root@ubuntu:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               VolGroup
  PV Size               298.09 GB / not usable 2.78 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              76310
  Free PE               0
  Allocated PE          76310
  PV UUID               HaIApD-ZnpM-hn30-5DWn-898Z-DOoQ-PM8oO4
   
  --- Physical volume ---
  PV Name               /dev/sdb5
  VG Name               VolGroup
  PV Size               295.99 GB / not usable 1.49 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              75773
  Free PE               0
  Allocated PE          75773
  PV UUID               tlzmO7-As83-jZzD-V4Mq-W7V8-2x9y-AilNGh

```

I tried shrinking the filesystem like so:
```

root@ubuntu:~# ext2resize /dev/sda1 300112m
ext2resize v1.1.19 - 2001/03/18 for EXT2FS 0.5b
error: End of Device: read 0 of 1024 bytes at 1024
root@ubuntu:~# 

```

And similarly:
```
root@ubuntu:~# resize2fs /dev/sda1 300112m
resize2fs 1.40.8 (13-Mar-2008)
resize2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
root@ubuntu:~# 

```

I'm doing this all from the Desktop live cd, so none of the volumes/partitions are mounted. I'm new to LVM, and it sounds promising (supposedly being able to easily resize partitions without losing data), so any help on this will be greatly appreciated. Like I said before, I've been searching on how to do this for a while now. Thanks in advance.

---

### Post by rowdog on 2008-09-08
Well, the first problem is that you're trying to resize an extended partion rather than the actual ext3 filesystem. I believe you need to get lvm and the device mapper running before you can resize a filesystem that's split across 2 disks.

PLEASE BE CAREFUL, DO NOT JUST COPY AND PASTE!!!

I'm no expert in LVM2 but here's what I'd try to do...


boot live cd and get a root shell
install lvm2 in the running system ... aptitude install lvm2
load the kernel module(s?) ... something like modprobe dm_mod
get an idea of the size of the fs you want to resize
  mount /dev/VolGroup/Whatever /mnt
  df -h /mnt
  umount /mnt
now, especially for ext3 you'll want some extra space because you need to store the journal. I usually add about 10G of safety margin.

check the filesystem ... e2fsck -f /dev/VolGroup/Whatever

now, you'll need to know the new size of the fs. Say that df -h said it was 120G, A lot of web sites say how to get the numbers right but I don't want to screw up my filesystems so I would then go with like 130G

resize2fs /dev/VolGroup/Whatever 130G

It's probably not necessary but I always run e2fsck again after resizing.

Now you can lvreduce the logical volume and then maybe even pvresize the physical volume if you want to take the space outside of lvm.

Good Luck!

---

