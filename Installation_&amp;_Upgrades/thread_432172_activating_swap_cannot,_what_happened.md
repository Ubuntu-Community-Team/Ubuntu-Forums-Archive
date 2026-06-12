---
title: "activating swap: cannot, what happened?"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by longbow on 2007-05-03
when my ubuntu 6.10 is booting, there is an message:
[COLOR="Blue"]activating swap                      cannot[/COLOR]

displayed. It seems the swap partition is not mounted correctly. Then the system can boot smoothly, and runs well.

So what has happened? has my swap partition been mounted correctly?
I checked the mount table, there is no swap partitions (as I remember, the swap partition should be mounted as /swap, right?). 
In the gnome partition editor, the status of the swap partition is good, its status is "active". 
And in the context menu for the swap partition, the availabel command is "swapoff", so it implies currently swap is on.
I've checked the /etc/fstab, the uuid is correct.

So, can anybody help me on how to figure out whether my swap partition is mounted correctly?
If not, how to fix it? 

thanks a lot.

---

### Post by taurus on 2007-05-03
Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by longbow on 2007-05-04
fdisk -l:    (I use sdb as my linux disk.)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5540    41882368+   7  HPFS/NTFS
/dev/sda2            9740       10337     4520880   12  Compaq diagnostics
/dev/sda3            5541        9739    31744440    f  W95 Ext'd (LBA)
/dev/sda5            5541        9739    31744408+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5099    40957686    7  HPFS/NTFS
/dev/sdb2   *        5100        9664    36668362+  83  Linux
/dev/sdb3            9665        9729      522112+  82  Linux swap / Solaris

etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=372fbfd6-8f6b-4a0a-9d52-43a3de221f16 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
# UUID=07D5-0C01  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
# UUID=C860D67560D66A28 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
# UUID=C8D8FE25D8FE1204 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# swap partition
UUID=e30c3d05-e4eb-4688-a1fd-77f24e68c3ee none            swap    sw              0       0
# /dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

# /dev/hda1, hda2, hda5, for zuozuo's x31.
# /dev/hda1 /media/hda1 ntfs umask=0222 0 0
# /dev/hda2 /media/hda2 ntfs umask=0222 0 0
# /dev/hda5 /media/hda5 ntfs umask=0222 0 0

---

### Post by longbow on 2007-05-06
anybody help???

---

### Post by taurus on 2007-05-06
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```
UUID=e30c3d05-e4eb-4688-a1fd-77f24e68c3ee none swap sw 0 0
```
with this one.

```
/dev/sdb3   none   swap   sw   0   0
```
Save it and reboot.  Then, run

```
free
```

---

