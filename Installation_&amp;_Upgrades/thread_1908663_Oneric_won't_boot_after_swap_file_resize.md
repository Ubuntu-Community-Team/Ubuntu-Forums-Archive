---
title: "Oneric won't boot after swap file resize"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by Scooter74 on 2012-01-13
Hi all. I'm having some issues after re-sizing my swap file. I have just done a clean install onto my 1TB machine with one large primary partition sba1 and just the extended/swap partitions sba2/sba5. I wanted to increase my swap file size. I used qparted to reduce my primary partition which was fine, I could boot and operate as normal. When I then enlarged my swap file I could not boot. It only gets to the BIOS stage where it starts the HD and stops there, it won't give a DD prompt or go to the GRUB menu.

When I try running the boot-repair from live CD it just freezes after spending about 10 minutes trying the inspect the drives. The drive mounts fine from live CD and I can see all the data but I can't fix it. Unfortunately I can't remember what the size of the old swap file was. Please help!

Thanks,
Scooter

---

### Post by Scooter74 on 2012-01-14
I also have another drive exactly the same that I use as a DD clone backup. Is there an easy way to create a new installation on that drive and import all the data and settings across? I've just spent days getting it all right so it would be a pity to lose it by doing another fresh install.

---

### Post by mikewhatever on 2012-01-14
[s]Try the 'nomodeset' parameter from the advanced options. To get to them, hit any key as soon as you see the purple background after the BIOS screen. That should interrupt the boot process and present a menu. Hitting f6 should bring up the advanced options.

If that doesn't work, post your hardware specs.[/s]

I've posted in a wrong thread, sorry.

-----------------------------------------------------------------------------

As for your problem, post the output of 'sudo fdisk -l' for a start. Something must have gone wrong with that swap partition. 
Hardware specs should not be relevant.

---

### Post by Scooter74 on 2012-01-14
I can't get as far as the purple screen but I'll post the hardware specs once the kids get off the computer. 

I've just done a fresh install onto the spare drive I mentioned earlier as well if that helps to solve this quicker. The fresh install works fine.

---

### Post by Scooter74 on 2012-01-14
sudo fdisk -l
```
Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a52e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1941506047   970752000   83  Linux
/dev/sda2      1941506048  1953523711     6008832    5  Extended

```

---

### Post by mikewhatever on 2012-01-14
The output shows that there is no swap partition, and no /dev/sda5 either.

You might want to try and disable swap altogether by commenting it out in fstab.
From the Live CD:

sudo mount /dev/sda1 /mnt

gksudo gedit /mnt/etc/fstab

...then, place '#' before the swap line, save and exit.

It should look something like this:
```

# swap was on /dev/sda5 during installation
#UUID=8ad5c16e-618f-4e31-bf59-0e8c00181654 none            swap    sw              0       0
```

Try booting the system now.

---

### Post by Scooter74 on 2012-01-14
This is the current fstab. I'll try commenting out and a reboot.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=fc35f79c-d09e-4eac-92df-d3137014e2cc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b39b509a-5756-4a37-a572-89c0f11fac5a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by Scooter74 on 2012-01-14
No good. I still have the same result.

Should the UUIDs be the same? I'm not sure how they work.

---

### Post by mikewhatever on 2012-01-14
> **Scooter74 said:**
> No good. I still have the same result.

Should the UUIDs be the same? I'm not sure how they work.

No, the UUID doesn't matter for commenting out a line. Yours should look as follows when commented out:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=fc35f79c-d09e-4eac-92df-d3137014e2cc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
**#**UUID=b39b509a-5756-4a37-a572-89c0f11fac5a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Note the '**#**' in the beginning of the line before last.

---

### Post by Scooter74 on 2012-01-14
Yep, no good. If I look at the disk through gparted it shows the whole thing as unallocated. Through disk utility it shows sda1 as normal and sda2 as an extended partition but it shows the swap file (that was inside the extended partition) as a capacity of 18446744TB of unallocated space. If I try to delete the extended partition I get this error.
```
Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sda, offset=994051096576
Entering MS-DOS parser (offset=0, size=1000203804160)
MSDOS_MAGIC found
looking at part 0 (offset 1048576, size 994050048000, type 0x83)
new part entry
looking at part 1 (offset 994051096576, size 6153043968, type 0x05)
Entering MS-DOS extended parser (offset=994051096576, size=6153043968)
readfrom = 994051096576
MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
partition to delete is an extended partition
got it
Error: Can't have a partition outside the disk!
ped_disk_new() failed

```

---

### Post by Scooter74 on 2012-01-14
I've just stumbled across some stuff on partition tables which seems to fit the bill.
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

Now I've just got to make sense of it and use sfdisk to fix the problem. This is the output of the PT.txt with this warning:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=1941504000, Id=83, bootable
/dev/sda2 : start=1941506048, size= 12017664, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
```

Can I simply change the /dev/sda2 line to:
/dev/sda2 : start=        0, size=        0, Id= 0

---

### Post by Scooter74 on 2012-01-14
I have now used fdisk to delete the old swap file and create a new one. I have fixed fstab to reflect the correct UUID but it still won't start and boot-repair still freezes when it is scanning.

I'm not sure if it is applicable but when I deleted the partition it gave this note:

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

PT.txt now shows```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=1941504000, Id=83, bootable
/dev/sda2 : start=1941506048, size= 12015616, Id=82
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
```
gparted and disk utility show the disk to be fine so I'm not sure if it is a partition table error or what. I'm guessing it isn't a grub issue because I can't even get to the purple screen

---

