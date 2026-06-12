---
title: "Cannot resolve UUID error"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by n4v33n on 2010-02-08
While my ubuntu starts up . He encounters filesystem errors caused my some like error which looks like this

Unable to resolve UUID 

This is what i get when i go 

sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45c545c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4844    38909398+  83  Linux
/dev/sda2            4845       30400   205278570    f  W95 Ext'd (LBA)
/dev/sda5            4845       17592   102398278+  82  Linux swap / Solaris
/dev/sda6           17593       30400   102880228+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

gedit /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7e4b7f93-4a63-4692-8c2f-db2caf055bc1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=1b473da1-ef4f-4cb5-a838-b6a1adabbd22 /opt            ext3    relatime        0       2
# /dev/sda6
UUID=8476162d-6213-4329-b7a1-0a9ebe66e054 /usr/local      ext3    relatime        0       2
# /dev/sda5
UUID=88139174-fcc1-4b7b-80f3-aca30418b8dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Basically out of 250 GB hard drive i see only 40 GB . Other drivers arent recognised for some reason

---

### Post by suseendran.rengabashyam on 2010-02-09
Hi,

Open the Terminal in your Ubuntu Machine and enter the following command:

```
sudo ls -o /dev/disk/by-uuid
```

The output will be something similar to:

```
lrwxrwxrwx 1 root 10 2010-02-10 00:01 047ef9b6-30d8-4807-8889-ofod2ebcc0b0 -> ../../sda5
```

Make a note of the various partitions and their respective UUID numbers. In my case it is '/dev/sda5' and '047ef9b6-30d8-4807-8889-ofod2ebcc0b0'.

Now open the /etc/fstab file and replace "UUID=047ef9b6-30d8-4807-8889-ofod2ebcc0b0" with "/dev/sda5".

Reboot you machine and see whether you get the same error.

Hope this helps.

---

