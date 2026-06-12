---
title: "Dualboot problems with 8.04 and Vista - Vista won't boot"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by bfeero on 2008-05-13
I am having troubles getting my computer to dual boot successfully. I have installed Ubuntu 8.04 on the first drive, with Vista Business on the other drive.

There is the section of my "menu.lst" that is pertinent:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows Vista x64
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0)   (hd1)
map             (hd1)   (hd0)
chainloader     +1
```

When I attempt to start Windows, the screen says "Starting up..." for a split second, then goes to black, then reboots. I assure you that Windows will boot when the second drive is attached alone.

Here is the result when I use "fdisk -l":

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23569   189317961   83  Linux
/dev/sda2           23570       24321     6040440    5  Extended
/dev/sda5           23570       24321     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3f850b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24791   199133676    7  HPFS/NTFS
```

... and my /etc/fstab....

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2be1474d-1e57-47e2-974f-e8c501cc068e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f5a6d187-ffc5-49f0-96ac-62649c4b96ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1 /media/VISTA ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Can anyone help?

-Brett

---

### Post by zanyspydude on 2008-05-13
> **bfeero said:**
> I am having troubles getting my computer to dual boot successfully. I have installed Ubuntu 8.04 on the first drive, with Vista Business on the other drive.

Can anyone help?

-Brett



Hey, i have the exact same problem as you and I'm going to try this solution.  Seems to be consensus view.  Hope it works for you (and me!)

[http://ubuntuforums.org/showthread.php?t=785651&highlight=dual+boot+vista](http://ubuntuforums.org/showthread.php?t=785651&highlight=dual+boot+vista)


other threads:

[http://ubuntuforums.org/showthread.php?t=787481&highlight=dual+boot+vista](http://ubuntuforums.org/showthread.php?t=787481&highlight=dual+boot+vista)

---

### Post by meierfra. on 2008-05-14
Try

title           Microsoft Windows Vista x64
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader     +1


as far as I know, Vista does not need the map lines (but Xp does)

If this does not work, please post the Ubuntu part of your menu.lst.

---

