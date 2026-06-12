---
title: "Automount FAT32 with music and pictures"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by user481516 on 2008-04-12
So, I have a fat32 drive with all my pictures and music on it.  I was wondering if there was an easy way to automount it on login.  Currently if I have a desktop background from the fat32 drive then it disappears when I unmount the drive.  How can I get it to show up automatically like my filesystem.  I have looked around in forums and things but I really don't understand them enough to risk messing with my computer in terminal.  Any help would be much appreciated, thanks ahead of time, Brian.

---

### Post by Oldsoldier2003 on 2008-04-13
> **briantadhorrocks said:**
> So, I have a fat32 drive with all my pictures and music on it.  I was wondering if there was an easy way to automount it on login.  Currently if I have a desktop background from the fat32 drive then it disappears when I unmount the drive.  How can I get it to show up automatically like my filesystem.  I have looked around in forums and things but I really don't understand them enough to risk messing with my computer in terminal.  Any help would be much appreciated, thanks ahead of time, Brian.

please post the results of
```
sudo fdisk -l
cat /etc/fstab
```

Then we can get you set up to have the partition mounted, and even toss in a soft link so that it shows up in your home directory.

---

### Post by warp99 on 2008-04-13
> **Oldsoldier2003 said:**
> please post the results of
```
sudo fdisk -l
cat /etc/fstab
```

Then we can get you set up to have the partition mounted, and even toss in a soft link so that it shows up in your home directory.

If the drive is a USB drive then you won't be able to setup the drive in the fstab because the devices in fstab occur before dbus and hal are loaded. The best way is to make an entry in /etc/rc.local to mount the drive.

---

### Post by terklotron on 2008-05-23
Hey guys.
I have the exact same problem. Althoug I do have some more harddrives. But I just need to automount the fat32 volume.

Output of fdisk -l

```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f7a3f79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14334   115137823+  83  Linux
/dev/sda2           14335       14946     4915890    5  Extended
/dev/sda5           14335       14946     4915858+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ab06d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2       25498   204804621    b  W95 FAT32
/dev/sdb6           25499       30401    39383316    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13911390

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14592   117210208+   7  HPFS/NTFS
```

Thank you

---

