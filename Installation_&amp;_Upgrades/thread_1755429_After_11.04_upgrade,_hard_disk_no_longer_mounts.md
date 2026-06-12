---
title: "After 11.04 upgrade, hard disk no longer mounts"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by RootsLINUX on 2011-05-11
I have one hard disk (call her HDA) that contains nothing but a single ext4 partition containing a backup of all my important data. I did a clean install of 10.10 on my primary hard disk (call her HDB) and from there proceeded to the 11.04 upgrade. In 10.10, I was able to read HDA just fine. However after the upgrade, I can no longer mount this drive. 

When mounting from file browser:
```

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The end of dmesg said the following:
```

dmesg | tail
[   49.853308] wlan0: associated
[   50.084874] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   52.859533] Intel AES-NI instructions are not detected.
[   52.890955] padlock_aes: VIA PadLock not detected.
[   60.710006] wlan0: no IPv6 routers present
[   82.130904] EXT4-fs (sda): bad geometry: block count 122096646 exceeds size of device (122096381 blocks)
[   96.010858] EXT4-fs (sda): bad geometry: block count 122096646 exceeds size of device (122096381 blocks)
[  107.791812] EXT4-fs (sda): bad geometry: block count 122096646 exceeds size of device (122096381 blocks)
[  322.758948] EXT4-fs (sda): bad geometry: block count 122096646 exceeds size of device (122096381 blocks)
[  516.932403] EXT4-fs (sda): bad geometry: block count 122096646 exceeds size of device (122096381 blocks)

```

Okay, so for some reason my hard disk has a block count greater than the size of my device. I've done my background searching on this and tried a command line utility I've never heard of before:

```

# sudo e2fsck /dev/sda
e2fsck 1.41.14 (22-Dec-2010)
The filesystem size (according to the superblock) is 122096646 blocks
The physical size of the device is 122096381 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

```


And this is as far as I've gotten. I'm really, really hesitant to start fiddling around and experimenting with possible fixes because the backup data on this drive holds a decade's worth of work for me and is extremely valuable (hence why I have a spare drive for backups). I really didn't think that the Ubuntu upgrade process would mess with this drive, seeing as the Ubuntu install was contained on an entirely different drive.


Can someone recommend for me the safest way for me to recover this data? Data preservation is the #1 priority for me here. I need to copy all of this data over to my primary drive where Ubuntu is installed. After that, I can reformat this "broken" backup drive without a care. Thanks in advance.

---

### Post by RootsLINUX on 2011-05-11
Did a little more reading and now I think it may be a bad partition table, not a bad super block. Still looking for help on how to restore my drive to working status.

-----

I used the following guide to try using a backup superblock to restore my disk.
[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

However, it failed complaining of the same problem. 
```

$ sudo fsck -b 32768 /dev/sda
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
The filesystem size (according to the superblock) is 122096646 blocks
The physical size of the device is 122096381 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

``` 

So if its not the super block that's corrupt, its probably the partition table, right? I found the following thread of someone else who experienced a very similar problem to me, although the cause of the problem was different (he was resizing a partition manually). I took a look at the partition table for my unmountable drive.
[http://gparted-forum.surf4.info/viewtopic.php?id=14172](http://gparted-forum.surf4.info/viewtopic.php?id=14172)

```

$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0

```

Wow. Well that doesn't look right. I used the Ubuntu disk utility to format the entire sda disk as a ext4 filesystem earlier (so I would assume that would only create a single partition?) and copied all my data there, then checked that I could access the data from the drive before I began my clean OS install.

Ran some fdisk commands on the drive as well to see if it had anything interesting to say.

List partition tables (yes, it shows no partitions):
```

$ sudo fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

```

Give partition size in blocks:
```

$ sudo fdisk -s /dev/sda 
488385527

```

---

### Post by Vomec on 2011-05-16
I've got the **EXACT** same problem here. Just upgraded to Ubuntu 11.04 and BAM!... Can't mount the disk. System on /dev/hdb (60GB ATA) and second disk /dev/hda (200GB ATA) with all my important data. I hope there is someone who can help because I even tried testdisk to "dig" my data back to external disk and reformat but even testdisk can't help me :(

---

### Post by rjwse on 2011-05-26
No 120GB USB external disk recognition after installing 11.04 on laptop.  At first, the 120 was okay.  I was copying files from it to the fresh install on the laptop.  The 120 is NTFS.  About half of the files transfered.  The others transferred at zero length.  The 120 will not mount.  Other disks get recognized by the laptop and I can transfer files back and forth from it to external USB 1TB disks and flash drives.  The 120 will not mount and I have begun searching the internet for the best way to proceed.  I do not know for sure if the 11.04 has anything to do with this problem.  It has never happened before.  There are some disk programs, but they are for experts, not novices.  If anyone has a solution on how to try to get back the 120 I would be grateful.

---

### Post by RootsLINUX on 2011-07-28
Months later after putting this off, I've solved my problem. The drive now mounts and I can access my data. The following steps are what I did to achieve this, and they were courtesy of the TestDisk support, which is a great application for data recovery.



I was suggested to do the following:

```


$ sudo fsck.ext4 /dev/sda
e2fsck 1.41.14 (22-Dec-2010)
The filesystem size (according to the superblock) is 122096646 blocks
The physical size of the device is 122096381 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

Backup contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Backup: 223131/30531584 files (0.1% non-contiguous), 44383187/122096646 blocks

$ sudo mkdir /mnt/backup

$ sudo mount -t ext4 /dev/sda /mnt/backup
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Looks familiar. And looking at dmesg | tail:

```

$ dmesg | tail
[359222.668707] EXT4-fs (sda): bad geometry: block count 122096646 exceeds size of device (122096381 blocks)

```

Also seen that before. I did some searching and thought that maybe using resize2fs (resize filesystem) was a command that could help. I asked if they thought this was correct and whether there was anything else I should try. They suggested I also try:

```

$ sudo mount -t ext4 -o ro /dev/sda /mnt/backup

```

Which failed the same way as the earlier mount attempt. Then I took a deep breath and resized the filesystem as he suggested:

```

$ sudo resize2fs /dev/sda 465G
resize2fs 1.41.14 (22-Dec-2010)
Resizing the filesystem on /dev/sda to 121896960 (4k) blocks.
The filesystem on /dev/sda is now 121896960 blocks long.

```

And after that, mounting my drive was successful and I can access all my data again! :D

---

