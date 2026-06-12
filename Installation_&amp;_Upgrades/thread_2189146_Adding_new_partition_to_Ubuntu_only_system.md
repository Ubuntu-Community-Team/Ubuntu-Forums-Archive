---
title: "Adding new partition to Ubuntu only system"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by jmarkrobinson on 2013-11-20
Objective:  To add two new partitions that will be used for user data only.
H/W:  Dell Dimension 9100 /Intel Pentium D (32bit dual core), 1Meg RAM
O/S:  Ubuntu-32 13.1

I need to add two partitions for data only and I'm not sure what to do.  I read somewhere that this should not be accomplished from the (Gparted) partition manager when executing Ubuntu from the HD.  I started to do it from the Ubuntu LiveCD, chose "Other" option but was not entirely sure that it would not destroy the existing installation that has already been customized.

Also, Gparted Live hangs during bootup on this machine.  (It's a localized issue with the machine that I have not been able to solve.  It won't boot to the Windows recovery disk, either.  And, yes, I have the CDR as the first device in the boot order.)  

Thanks in advance for any assistance from the Ubuntu gurus.

---

### Post by fantab on 2013-11-20
Yes, you must use Ubuntu LiveCD/DVD/USB, 'Try Ubuntu without installing'. Open Gparted and resize. Resizing partitions from left of the slider is never a good idea, only from right will be relatively safer.

However, before you proceed, post the output of the following:
```
sudo fdisk -l
sudo parted -l
```

Managing partitions can be RISKY for your DATA. So, before you do anything with Partitions BACKUP all your important DATA, to an External Device.

---

### Post by papibe on 2013-11-20
Hi jmarkrobinson.

First of all, backup your important data before any major changes to the disk partitions.

Yes. Use the Ubuntu Installation media as a Live CD/USB. Choose 'Try Ubuntu before install' or an option named similar than that. You should end up on the desktop.

There you can load Gparted (it is included on the CD), and make the changes you need. I would recommend not changing your root partition as you may need to update grub before rebooting (shrinking it is fine, but moving it may requiere the extra work).

Hope that helps. Let us know how it goes.
Regards.

P.S.: don't forget to back up your data ;)

---

### Post by jmarkrobinson on 2013-11-21
> **fantab said:**
> However, before you proceed, post the output of the following:
```
sudo fdisk -l
sudo parted -l
```

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c202

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312498175   155998209    5  Extended
/dev/sda5          501760   312498175   155998208   8e  Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 158.6 GB, 158628577280 bytes
255 heads, 63 sectors/track, 19285 cylinders, total 309821440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 1069 MB, 1069547520 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2088960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
```

------------------------------------------------------
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD1600JS-75M (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   160GB  160GB  extended
 5      257MB   160GB  160GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 1070MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  1070MB  1070MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 159GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  159GB  159GB  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
```

---

### Post by fantab on 2013-11-21
So you have LVM filesystem. I don't have much experience with LVM, however it seems fairly simple [READ HERE]("https://wiki.ubuntu.com/Lvm")... 

You might find this useful too:
[http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume)

Remember to **BACKUP your important DATA** first, preferably on an External Device.

Good Luck.

---

### Post by jmarkrobinson on 2013-11-21
Hmmm, something new to learn.  So much for getting this done quickly :-)  I installed Ubuntu on this box two weeks ago with defaults, I didn't choose LVM.  That's OK, looks like it is more flexible.

---

### Post by fantab on 2013-11-21
I don't think Ubuntu installer, by default, formats partition with LVM. You must have either used a distro from 'Fedora' family or made a mistake somewhere.

---

### Post by jmarkrobinson on 2013-11-22
Ubuntu 13.0 distro and I just followed the default instructions. Hardly an error when it setup with a more flexible file system :-)

---

