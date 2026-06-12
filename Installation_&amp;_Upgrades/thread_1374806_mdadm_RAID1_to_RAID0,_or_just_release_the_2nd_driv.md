---
title: "mdadm: RAID1 to RAID0, or just release the 2nd drive"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by hmhef on 2010-01-07
hi

i want to be able to use all that space that is mirrored in the /home folder 
(either raid0, or have 2 partitions)
i understand that /home is mounted on /dev/md2 ( /dev/sda2 + /dev/sdb2)

i have NO physical access to the server, and i plan to do it while logged on as root, so i can unmount the home folder while doing it

my question is
is that possible to do ? 
if yes, how ?


running ubuntu 8.04 desktop x86 tls

fdisk -l


```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000984bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         653     5242880   fd  Linux RAID autodetect
Partition 1 does not end on cylinder boundary.
/dev/sda2             653       60736   482615296   fd  Linux RAID autodetect
/dev/sda3           60736       60801      525856   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002c088

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         653     5242880   fd  Linux RAID autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdb2             653       60736   482615296   fd  Linux RAID autodetect
/dev/sdb3           60736       60801      525856   82  Linux swap / Solaris

Disk /dev/md2: 494.1 GB, 494197997568 bytes
2 heads, 4 sectors/track, 120653808 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 5368 MB, 5368643584 bytes
2 heads, 4 sectors/track, 1310704 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
```

df -a

```

Filesystem           1K-blocks      Used Available Use% Mounted on
rootfs                 5201472   3110740   1828592  63% /
/dev/root              5201472   3110740   1828592  63% /
proc                         0         0         0   -  /proc
sysfs                        0         0         0   -  /sys
tmpfs                  1023116        92   1023024   1% /var/run
tmpfs                  1023116         0   1023116   0% /var/lock
/dev/root              5201472   3110740   1828592  63% /dev/.static/dev
udev                   1023116        36   1023080   1% /dev
tmpfs                  1023116         0   1023116   0% /dev/shm
devpts                       0         0         0   -  /dev/pts
tmpfs                  1023116        92   1023024   1% /var/run
tmpfs                  1023116         0   1023116   0% /var/lock
/dev/md2             478812216   8255436 446426020   2% /home
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc

```

 cat /etc/fstab
```

/dev/md1       /       ext3    errors=remount-ro       0       1
/dev/md2       /home   ext3    defaults                0       2
/dev/sda3       none    swap    defaults        0       0
/dev/sdb3       none    swap    defaults        0       0
proc            /proc   proc    defaults        0       0
sysfs           /sys    sysfs   defaults        0       0

```

---

