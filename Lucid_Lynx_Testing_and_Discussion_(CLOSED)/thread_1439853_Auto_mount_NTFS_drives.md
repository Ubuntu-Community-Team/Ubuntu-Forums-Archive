---
title: "Auto mount NTFS drives"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 0004tom on 2010-03-26
I've been using the beta 1 build for a few days now, and WOW it's stupid fast. I've noticed from karmic when you go to Places > Drive your not asked to enter admin password. I used NTFS Conf in karmic to auto mount my 3 NTFS drives. I tried this in 10.04, but when I did I lost write access and ownership of the drive.

Is there something I cam do in fstab to auto mount the drives on boot?

My current FSTAB

```
 # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=9d46e43c-965b-4162-8ea2-5d1ee47b9ba2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=5e422c12-08a1-4273-b070-f672289ba570 none            swap    sw              0       0
```

and fdisk -l 

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x955d2d16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30402   244093952    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f36c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23330   187395072   83  Linux
/dev/sdb2           23330       24322     7963648+   5  Extended
/dev/sdb5           23330       24322     7963648   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1b5f69c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488383488    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45f1bef2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60802   488383488    7  HPFS/NTFS
```

Thanks in advance

---

### Post by voja15 on 2010-03-26
I am using karmic, but nevertheless I think this should work:
Open terminal and type:
```
sudo gedit /etc/fstab
```
At the end of fstab file add the folowing line:
```
/dev/sda5                                  /media/sda5    ntfs         defaults                                                0  0 
```
Where /dev/sda5 is the path to your drive, and /media/sda5 is the mount point. (as I can see from your fdisk -l, I guess you want to mount sda1,sda2,sdc1,sdd1)
If that doesn't work, try setting the file and dir mode in parameters:
```
/dev/sda5                                  /media/sda5    ntfs iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
If it's a network share, use cifs instead of ntfs.

Hope this helps.

---

### Post by seeker5528 on 2010-03-26
Looking at '/usr/share/doc/ntfs-3g/README.Debian' since I am not at home right now, something like:

```
/dev/sda1  /mnt/sda1  ntfs-3g  silent,umask=0,locale=en_US.utf8  0  0
```

works for me, I think if you don't specify the locale, whatever is set as the system wide default will be used.

If you install mount manager and use it to set up the mounts, that works as well.

Later, Seeker

---

