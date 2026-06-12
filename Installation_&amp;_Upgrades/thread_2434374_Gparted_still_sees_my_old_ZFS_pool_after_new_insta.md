---
title: "Gparted still sees my old ZFS pool after new install on etx4 / xfs"
date: 2020-01-04
forum: Installation &amp; Upgrades
---

### Post by cdysthe on 2020-01-04
Hi,

I got a new laptop with a 500 GB SSD. I decided to check out ZFS on Ubuntu 19.10 and installed choosing the new option for ZFS install. All went well and it all worked. I played around with ZFS for a little while but wanted to get back to my old disk layout so I started the installer again, chose "something else" and reused the EFI partition. I then created a small ext4 /boot partition and a large xfs / partition for everything else with. I use a swapfile so no swap partition. All went well (I have done this many times before). The laptop runs fine. Then I wanted to look at the disk layout with GParted, and this is what I see:

[ATTACH=CONFIG]284744[/ATTACH]


However using parted I see this:

```
Model: WDC PC SN730 SDBQNTY-512G-1001 (nvme)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
 2      538MB   1088MB  551MB  ext4         boot
 3      1088MB  512GB   511GB  xfs

```

Blkid outputs:

:```
/dev/nvme0n1p3: LABEL="xfs" UUID="2d5ba3d0-d9ef-4465-8cfa-67fe87b6c791" TYPE="xfs" PARTUUID="7d315998-bf5c-48a9-b061-fea86c00a2f0"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/nvme0n1p1: LABEL_FATBOOT="EFI" LABEL="EFI" UUID="E066-6430" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="33001af0-5295-43a8-80ed-0ad7a12690e8"
/dev/nvme0n1p2: LABEL="ext4" UUID="11c60a5e-1b2f-4278-ad3b-c7dc475a17dd" TYPE="ext4" PARTLABEL="boot" PARTUUID="1c1aa0fa-3f1e-4274-8f76-060bb748bad1"

```

and finally fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p3 during installation
UUID=2d5ba3d0-d9ef-4465-8cfa-67fe87b6c791 /               xfs     defaults        0       0
# /boot was on /dev/nvme0n1p2 during installation
UUID=11c60a5e-1b2f-4278-ad3b-c7dc475a17dd /boot           ext4    defaults        0       2
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=E066-6430  /boot/efi       vfat    umask=0077      0       1
/swapfile 
```

What is going on here and I how can I get rid of the ZFS "ghosts" on my disk hopefully without having to do a wipe, format and new install. I could of course avoid GParted, but I feel uneasy having these ghosts from the past somewhere deep down on  my drive.

---

### Post by averyfreeman on 2020-01-31
When you prepped the drive did you run 'wipefs -a'?  I'd wipe it that way and delete+create a new partition table in fdisk, too.  Sometimes that lingering stuff is hard to get rid of.

If you have another drive, maybe you can clone your current drive and then clone the backup after you're finished cleaning the partition. Here's an example: [http://positon.org/clone-a-linux-system-install-to-another-computer](http://positon.org/clone-a-linux-system-install-to-another-computer)

---

### Post by cdysthe on 2020-01-31
> **averyfreeman said:**
> When you prepped the drive did you run 'wipefs -a'?  I'd wipe it that way and delete+create a new partition table in fdisk, too.  Sometimes that lingering stuff is hard to get rid of.

If you have another drive, maybe you can clone your current drive and then clone the backup after you're finished cleaning the partition. Here's an example: [http://positon.org/clone-a-linux-system-install-to-another-computer](http://positon.org/clone-a-linux-system-install-to-another-computer)


No, I didn't do anything except for letting the Ubuntu installer create new partitions but kept EFI. I've been using the machine since then without problems other than with Gparted. I will try what you suggested and report back. 

Kinda irks me how "deep" ZFS goes into the disk but that's probably because I do not get that file system. I do not think I need to either unless I go BSD..

---

