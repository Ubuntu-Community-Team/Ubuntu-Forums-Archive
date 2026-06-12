---
title: "Partition mounting"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by Elvish Legion on 2007-01-20
I just set up a dual boot, and would like to copy some files off my windows partition, but it isn't listed in my fstab, how would I go about fidning the info I need then adding it to fstab?

---

### Post by aysiu on 2007-01-20
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by taurus on 2007-01-20
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Elvish Legion on 2007-01-20
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9348    75087778+   c  W95 FAT32 (LBA)
/dev/hda2           14038       14593     4466070    5  Extended
/dev/hda3   *        9349       14037    37664392+  83  Linux
/dev/hda5           14241       14593     2835441   82  Linux swap / Solaris
/dev/hda6           14038       14240     1630534+  82  Linux swap / Solaris

Partition table entries are not in disk order

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=68f2c347-7926-49e0-9804-f1370a42f44d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=e3a2629d-79be-4a53-8734-b5de92a7f234 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


I don't see hda1 listed in my fstab

---

### Post by taurus on 2007-01-20
```
gksudo gedit /etc/fstab
```
Add this line to the end of it.

```
/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Then create a mount point and mount it.

```
sudo mkdir /media/hda1
sudo mount -a
df -h
```

p.s.  You have two swap partitions!

---

### Post by Elvish Legion on 2007-01-20
> **taurus said:**
> ```
gksudo gedit /etc/fstab
```
Add this line to the end of it.

```
/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Then create a mount point and mount it.

```
sudo mkdir /media/hda1
sudo mount -a
df -h
```

p.s.  You have two swap partitions!


Thanks much

Now to get the folder copied and see if I can get playing on linux

---

