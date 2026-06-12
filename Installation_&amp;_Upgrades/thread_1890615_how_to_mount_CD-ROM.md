---
title: "how to mount CD-ROM??"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by Sorebas on 2011-12-03
I googled, but I can't solve my problem.


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=fd53229e-236c-433b-8460-3358d2cba738 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=538ddaab-ecb4-49e9-ac8e-5d1728a8db08 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xae79ae79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9732    57689415    f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   b  W95 FAT32
/dev/sda6            5101        9732    37206508+   7  HPFS/NTFS

---

### Post by LycoLoco on 2011-12-03
Hi! Are you wanting to mount an ISO file, such as an Ubuntu Live CD or install DVD? If so you can follow this wiki article:

[https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso)

As it shows there you'll want to use the following commands, and if you want to know why you're running each one you can read the article (I highly recommend it).

$ sudo mkdir /media/example
$ sudo mount -o loop file.iso /media/example 
$ sudo mount -o rw,loop file.iso /media/example

To Unmount
$ sudo umount /media/example
$ sudo rmdir /media/example

If you're wanting to mount what's in the tray (a physical disc), then you'll want to mount your cd device

$ sudo mount -t iso9660 /dev/YOURDEVICE /media/example

Hope that helps!

(By the way, I'm sure this question has been answered on the forums before. Next time save yourself a bit of time and search first. That way you'll get your answer faster and you'll become familiar with what search terms work for finding answers. Happy answer hunting!)

---

