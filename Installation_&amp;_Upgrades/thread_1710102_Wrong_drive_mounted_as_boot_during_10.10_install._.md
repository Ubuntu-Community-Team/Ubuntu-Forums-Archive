---
title: "Wrong drive mounted as /boot during 10.10 install. How do I resolve?"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by KillrBuckeye on 2011-03-19
My old server machine running Ubuntu 6 experienced hardware failure, so I built a new machine with spare parts and decided to install 10.10.  I used the 2 HDDs from the old machine and decided to use existing partitions for the 10.10 installation.  I specified the existing partitions on a 250 GB PATA drive for root, /boot, /home, and swap.  For some reason when I booted up 10.10 for the first time, the other HDD (750 GB SATA) was mounted as /boot.  I never specified the second drive to be used for anything during the installation, so I have no idea why this happened.  

Any ideas why this happened, and how can I change the mount point for /boot?  I would like the highlighted partition in the attached screenshot to be /boot.  I really hope nothing on the 750 GB drive was overwritten in this whole process, because it contains all of my photo and video backup.

Any help you can provide would be appreciated.

---

### Post by KillrBuckeye on 2011-03-19
Now I'm even more confused.  The drive designations in /etc/fstab and the output of fdisk -l don't seem to match:

Here's my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb5       /               ext4    errors=remount-ro 0       1
/dev/sdb1       /boot           ext4    defaults        0       2
# /home was on /dev/sdb2 during installation
UUID=387f4854-fa08-4530-8435-33d9d597db33 /home           ext3    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=68d453dc-d2bd-465d-8ad8-fd9b71c5277f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Here's output of fdisk -l
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ce7ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          51      409626   83  Linux
/dev/sda2              52        1963    15358140   83  Linux
/dev/sda3            1964        2059      771120   82  Linux swap / Solaris
/dev/sda4            2060       28830   215038027    5  Extended
/dev/sda5            2060        3334    10241406   83  Linux
/dev/sda6            3335       28830   204796588+  83  Linux

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00038666

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

```

In one place my 250 GB drive with multiple partitions is being called sda, and in the other place it's sdb...

---

