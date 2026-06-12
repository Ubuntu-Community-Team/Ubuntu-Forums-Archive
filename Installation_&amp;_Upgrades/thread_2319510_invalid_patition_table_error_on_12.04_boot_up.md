---
title: "invalid patition table error on 12.04 boot up"
date: 2016-04-04
forum: Installation &amp; Upgrades
---

### Post by soar2 on 2016-04-04
Hi, all:
    MY PC have a RAID card and 2 500G hard disks. I created  a RAID1 disk then  install ubuntu 12.04 on it. But the PC prompt 'Invalid Partition Table!' and 
stop when boot, if press ESC or F5, the ubuntu  can start up. How to fixed this error? 
```

# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000edbe5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   943368191   471683072   83  Linux
/dev/sda2       943370238   976766975    16698369    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       943370240   976766975    16698368   82  Linux swap / Solaris


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000edbe5


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   943368191   471683072   83  Linux
/dev/sdb2       943370238   976766975    16698369    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5       943370240   976766975    16698368   82  Linux swap / Solaris


Disk /dev/mapper/isw_dfciehgfed_Volume0: 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976767240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000edbe5


                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dfciehgfed_Volume0p1            2048   943368191   471683072   83  Linux
/dev/mapper/isw_dfciehgfed_Volume0p2       943370238   976766975    16698369    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_dfciehgfed_Volume0p5       943370240   976766975    16698368   82  Linux swap / Solaris


Disk /dev/mapper/isw_dfciehgfed_Volume0p1: 483.0 GB, 483003465728 bytes
255 heads, 63 sectors/track, 58721 cylinders, total 943366144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/isw_dfciehgfed_Volume0p1 doesn't contain a valid partition table
fdisk: unable to read /dev/mapper/isw_dfciehgfed_Volume0p2: Inappropriate ioctl for device
root@kr:~# mount
/dev/mapper/isw_dfciehgfed_Volume0p1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/x/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=x)

```

Thanks!

Regards,
soar

---

### Post by soar2 on 2016-04-06
use boot repair tools reinstall the grub into "/dev/mapper/isw_dfciehgfed_Volume0p1" disk can solve the problem!

---

