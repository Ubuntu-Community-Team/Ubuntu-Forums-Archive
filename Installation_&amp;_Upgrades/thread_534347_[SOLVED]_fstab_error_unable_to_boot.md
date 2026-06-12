---
title: "[SOLVED] fstab error? unable to boot"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by notwen on 2007-08-25
So I have backed up data from a 3rd hdd's partition to wipe it of 3 partitions to create 1 large partition.  After doing so using the gparted livecd I can no longer boot my system.

Here are the results of my "sudo fdisk -l"
---
```

Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        1867    14996646   83  Linux
/dev/hdc2            1868        9830    63962797+  83  Linux
/dev/hdc3            9831        9964     1076355   82  Linux swap / Solaris

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36483   293049666   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux

```

hdc1 is my / partition
hdc2 is my /home partition
hdc3 is my swap

sda1 is a media partition
sdb1 is my new large partition created in gparted.

Is there any simple way to correct this? If possible I would like to avoid wiping my hdc hdd. Thanks for anything you may have to offer. =]

---

### Post by merlinus on 2007-08-25
Use gparted live cd to set the boot flag on hdc1.

Also, you posted sudo fdisk -l, not /etc/fstab.

-merlin

---

### Post by notwen on 2007-08-25
Gave hdc1 the boot flag, still not working.  Here is my /etc/fstab, I'm guessing I will need to modify the two sdb entries, being there is only sdb1 now.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=46820649-a3cd-48e5-9c13-5de89dc38fda /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc2
UUID=eb0af0e3-eeba-4b35-8191-adb791161882 /home           ext3    defaults        0       2
# /dev/sda1
UUID=d8e6b25d-fc55-4d1f-824a-653ac4e769f2 /media/sda1     ext3    defaults        0       2
# /dev/sdb1
UUID=8DB2-371A  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=4d20342f-52f9-40ff-ab54-a91b1a59e459 /media/sdb2     ext3    defaults        0       2
# /dev/hdc3
UUID=bf6523e9-04c0-43b5-aa03-c953b6a02770 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto  0       0

```

---

### Post by notwen on 2007-08-25
here is my current fstab which i am about to try

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=46820649-a3cd-48e5-9c13-5de89dc38fda /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc2
UUID=eb0af0e3-eeba-4b35-8191-adb791161882 /home           ext3    defaults        0       2
# /dev/sda1
/dev/sda1 /media/sda1     ext3    defaults        0       2
# /dev/sdb1
/dev/sdb1 /media/sdb1     ext3    defaults        0       2
# /dev/hdc3
UUID=bf6523e9-04c0-43b5-aa03-c953b6a02770 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto  0       0

```

---EDIT---

all is working now, i simply modified the sda1 and sdb entrie son my /etc/fstab and changed the UUIDs to the corresponding /dev/sda1 and /dev/sdb1.

Huge thanks to zyth on freenode. =]

---

