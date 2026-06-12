---
title: "[SOLVED] JFS Slave Hard Drive, not mounting."
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by perlluver on 2008-09-18
Ok, looked through these posts, and searched, couldn't find anything pertaining to JFS.  Simply the JFS slave drive will not mount.  It is visible in sudo fdisk -l, shown as /dev/sda1: ```
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdb77fba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4865    39078081   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24134   193856323+  83  Linux
/dev/sdb2           24135       24321     1502077+   5  Extended
/dev/sdb5           24135       24321     1502046   82  Linux swap / Solaris
```

When trying to mount, this is displayed, even when added to fstab: ```
sudo mount /dev/sda1 /media/disk
mount: special device /dev/sda1 does not exist
```

Any help would greatly be appreciated.  I know the hard drive is good for it works in Hardy, and I know it is an aplha, but still would think it would mount.

I have also changed the Prefs, under mount so that I can mount.

---

### Post by perlluver on 2008-09-18
Alright I am going to wait on Intrepid, until beta 4 maybe.

---

