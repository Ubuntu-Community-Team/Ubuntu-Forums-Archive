---
title: "Upgraded from Karmic to Lucid, not seeing external and internal HDD"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by stegouin on 2010-05-01
I did receive a few errors during upgrade process, one of which was relating to GRUB.

I currently have 2 internal disks, my primary has OS on it, 80GB, secondary is 500gb, both are ect4 filesystem.

My external is 500 firewire 400 and NTFS.

Contents of my /etc/fstab/

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=cfbd22cc-b008-432f-93b1-df614d49ca41 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bf4c544d-c7a0-40c5-859f-489787958763 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```Not seeing any mount points for my internal and external drives

sudo fdisk -l reveals the following info:
```

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0fe90fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9359    75176136   83  Linux
/dev/sda2            9360        9733     3004155    5  Extended
/dev/sda5            9360        9733     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc29835b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

```Any ideas? I don't have dual boot, this is a full Linux ext4 system (with the exception of external HDD)

Thanks for any help

---

### Post by efflandt on 2010-05-01
Not quite what you are expecting or looking for.  Drives that you do not specifically configure mount points for during installation, or or not added to /etc/fstab yourself, are typically auto mounted on the fly, either when you access them if internal or present during boot, or when you connect external drives if plugged in later.

You have given no indication whether anything shows up for them in the **mount** command.

Do they show up in the **Places** menu, or whatever file navigator is in whichever window manager you are running?

---

### Post by stegouin on 2010-05-01
Thanks for the reply... no the drives don't show up under "Places"... 

I do recall during the upgrade process when Grub2 step was executed, it had listed all available mount points and prompted for selection to include in Grub2 config... I basically selected all of them (as recommended on the screen)... that's when an error occurred.

I assume a log of the upgrade process is written somewhere, but I have no clue where. I will search and see, and post any relevant messages..

---

