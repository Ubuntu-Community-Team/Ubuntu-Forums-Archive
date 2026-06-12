---
title: "Ubuntu installer doesn't list drive, but it shows up in GParted"
date: 2018-07-26
forum: Installation &amp; Upgrades
---

### Post by zacharygillenwater on 2018-07-26
Hello, I'm currently attempting to install Lubuntu 18.04 on my PC and having a bit of trouble. I'm currently trying to install to a secondary hard drive to my main Windows drive, but for some reason the installer seems incapable of actually seeing this drive, even though GParted, Parted, and fdisk all list it and can manipulate it.

I can, however, select the drive as the location for the bootloader.

fdisk -l outputs the following (this is with my main HDD physically unplugged from my motherboard, so only my secondary HDD and the live flash drive are connected):

```
Disk /dev/loop0: 967.6 MiB, 1014571008 bytes, 1981584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x91f1711d

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1        2048 976773119 976771072 465.8G 83 Linux


Disk /dev/sdb: 3.8 GiB, 4089446400 bytes, 7987200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x67e97428

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *        0 2111199 2111200    1G  0 Empty
/dev/sdb2       12152   16823    4672  2.3M ef EFI (FAT-12/16/32)
```

/dev/sda is the drive I'm attempting to install to, /dev/sdb is the live USB drive

Any suggestions? I've mounted the drive, removed a hidden flag that was for some reason applied, used NTSF and ext4 formats, and obviously tried with my main drive connected and disconnected. I can't figure out what's wrong and have had no luck finding similar issues online. Thanks.

---

### Post by izznogooood on 2018-07-26
Have you tried installing from the Live Environment ?

---

### Post by zacharygillenwater on 2018-07-26
Yep, that's how I know that the disk is listed in fdisk. So even the live environment appears to know that the HDD exists, but for some reason the installer doesn't allow it as the drive to install the OS to.

---

### Post by izznogooood on 2018-07-26
This is very strange in deed....

If you can:

Try and nuke the drive from "disks" and re-initialize with a GPT partition table.
Then download a daily build from: [http://cdimage.ubuntu.com/bionic/daily-live/current/](http://cdimage.ubuntu.com/bionic/daily-live/current/)

Try in live again...

If this does not work I suggest filing a bug @ [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) (skimm it, dont be deterred... )

---

### Post by zacharygillenwater on 2018-07-26
That did it! For some reason changing the partition table from msdos to GPT made it show up in the installer. I'm now enjoying a super fast install of Lubuntu - Thanks!

---

