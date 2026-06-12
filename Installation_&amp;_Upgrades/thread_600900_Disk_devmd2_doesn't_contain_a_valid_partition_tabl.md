---
title: "Disk /dev/md2 doesn't contain a valid partition table"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by gian on 2007-11-02
Hello,

I needed a backup for my pictures, so I installed Ubuntu from 7.10 alternate on a 4 SATA2 drives pc.
During install, I followed instructions in order to create a software RAID1 array with no spares.

I partitioned like this:
array 1
/ 24GB
swap 2 GB
/home 376GB
array 2
/cinema 400GB

here's fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md2
UUID=85bf6da0-d4d5-4bc6-b07e-e380118cc660 /               ext3    defaults,errors=remount-ro 0       1
# /dev/md1
UUID=0f958b0a-cdda-4d38-95e7-07cd9ddc1b4c /cinema         ext3    defaults        0       2
# /dev/md4
UUID=f53292ce-698b-4349-b986-d1676bb797b6 /home           ext3    defaults        0       2
# /dev/md3
UUID=b2561849-2c7a-4f3f-b786-5d63cbd29a37 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

here's mdstat:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdc1[0] sdd1[1]
      390708736 blocks [2/2] [UU]
      
md4 : active raid1 sda3[0] sdb3[1]
      365221632 blocks [2/2] [UU]
      
md3 : active raid1 sda2[0] sdb2[1]
      1951808 blocks [2/2] [UU]
      
md2 : active raid1 sda1[0] sdb1[1]
      23535104 blocks [2/2] [UU]
      
unused devices: <none>

here's mount:
/dev/md2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/md1 on /cinema type ext3 (rw)
/dev/md4 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)

and here's fdisk:


Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00071224

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2930    23535193+  fd  Linux raid autodetect
/dev/sda2            2931        3173     1951897+  fd  Linux raid autodetect
/dev/sda3            3174       48641   365221710   fd  Linux raid autodetect

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076a10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2930    23535193+  fd  Linux raid autodetect
/dev/sdb2            2931        3173     1951897+  fd  Linux raid autodetect
/dev/sdb3            3174       48641   365221710   fd  Linux raid autodetect

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007e03c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/md2: 24.0 GB, 24099946496 bytes
2 heads, 4 sectors/track, 5883776 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md3: 1998 MB, 1998651392 bytes
2 heads, 4 sectors/track, 487952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md4: 373.9 GB, 373986951168 bytes
2 heads, 4 sectors/track, 91305408 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md1: 400.0 GB, 400085745664 bytes
2 heads, 4 sectors/track, 97677184 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Now, at the end of FDISK I get this errors:
Disk /dev/md2 doesn't contain a valid partition table
Disk /dev/md3 doesn't contain a valid partition table
Disk /dev/md4 doesn't contain a valid partition table
Disk /dev/md1 doesn't contain a valid partition table

Question: should I worry?
I have searched for this error, but could not find a straight answer.
Everything works fine, boot included.

Also, I could not avoid the system to create as first array (md1) the data disk, while the OS is on md2, swap on md3 and home on md4. Tried twice, but it always come out this way.
It's just unaesthetic, but I would have preferred the OS to be md1.

BTW, did I do any strategic/logic error so far?

*thanks* for your time,
regards,
-Gian

---

### Post by gian on 2007-11-03
<bump>

---

### Post by gian on 2007-11-05
<bump><bump>

---

