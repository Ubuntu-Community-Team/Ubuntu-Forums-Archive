---
title: "unknown filesystem after command"
date: 2013-01-26
forum: Installation &amp; Upgrades
---

### Post by blueeyeblue on 2013-01-26
Hi gals and guys!

I've wanted to fix some problems, e.g. Linux loads only sometimes upon restart and since I've executed ```
sudo fsck -yv /dev/sda1
```I can't restart PC anymore.

All what I see is just ```
error: unknown fileystem.
grub rescue> _
```


I've tried to fix it with Live CD with no luck.

Here is fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfa1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19087   153312256   83  Linux
/dev/sda2           19087       19458     2975745    5  Extended
/dev/sda5           19087       19458     2975744   82  Linux swap / Solaris

Disk /dev/sdb: 61.9 GB, 61918150656 bytes
255 heads, 63 sectors/track, 7527 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20455945

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7527    60460596    c  W95 FAT32 (LBA)

Disk /dev/sdc: 1997 MB, 1997537280 bytes
255 heads, 63 sectors/track, 242 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         243     1950656    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(241, 254, 63) logical=(242, 217, 39)

```

and fdisk -lu
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfa1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   306626559   153312256   83  Linux
/dev/sda2       306628606   312580095     2975745    5  Extended
/dev/sda5       306628608   312580095     2975744   82  Linux swap / Solaris

Disk /dev/sdb: 61.9 GB, 61918150656 bytes
255 heads, 63 sectors/track, 7527 cylinders, total 120933888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20455945

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   120921254    60460596    c  W95 FAT32 (LBA)

Disk /dev/sdc: 1997 MB, 1997537280 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3901440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *         128     3901439     1950656    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(241, 254, 63) logical=(242, 217, 39)

```


I'd like to have my system working again, without reinstalling it.


Thank you all in advance for your help!

---

### Post by Herman on 2013-01-26
You can use 'Disk Utility' in the LiveCD to check on your disks and see if they're healthy from a hardware point of view, I think it's quite helpful and may save you some time. 
Some brands of hard disks are known to show up as bad even when they are normal. Any suspected problems need to be confirmed with other commands. Due to the proprietary nature of some hard disk firmware, it's not possible to read the disk's report accurately without the manufacturer's own special software.

The blkid command should tell you what file system is in /dev/sda1, I assume it will be ext4 which is currently the most popular.

For an ext series file system try 'sudo e2fsck -C0 -f -v -p /dev/sda1', that command will only run a quick check and 'preen' your file system. It will also print out a verbose output for you which will either tell you your file system is okay or suggest to you another command which you can use to try to fix it.

---

### Post by grahammechanical on 2013-01-26
Do you get a Grub menu? Can you select Recovery mode? Can you select an earlier kernel? How about telling us the version of Ubuntu that you are using? How about the hardware specs?

See, if this can help you

[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemix")

Note the Boot-Repair Utility that comes with it.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by blueeyeblue on 2013-01-27
> **Herman said:**
> You can use 'Disk Utility' in the LiveCD to check on your disks and see if they're healthy from a hardware point of view, I think it's quite helpful and may save you some time. 
Some brands of hard disks are known to show up as bad even when they are normal. Any suspected problems need to be confirmed with other commands. Due to the proprietary nature of some hard disk firmware, it's not possible to read the disk's report accurately without the manufacturer's own special software.

The blkid command should tell you what file system is in /dev/sda1, I assume it will be ext4 which is currently the most popular.

For an ext series file system try 'sudo e2fsck -C0 -f -v -p /dev/sda1', that command will only run a quick check and 'preen' your file system. It will also print out a verbose output for you which will either tell you your file system is okay or suggest to you another command which you can use to try to fix it.


I've did what you suggested.

```
root@blueeyeblue:~# sudo e2fsck -C0 -f -v -p /dev/sda1
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;


```

I'cant access disk somehow. I've also tried accessing disk from live cd. It does not work. Maybe some blocks are corrupted?

Ubuntu version is 10.04.
I've also tried Boot Repair with no luck.


Thanks for help!

---

### Post by blueeyeblue on 2013-01-27
Nevermind, I actually gave up. There were many unresolved problems, similar to: [http://ubuntuforums.org/showthread.php?t=2103621](http://ubuntuforums.org/showthread.php?t=2103621) and many more.

So finally I installed Win 8 with custom GMA 950 drivers for my Acer Aspire One D150-Bk.


Thank you all for your help anyway.

---

### Post by Herman on 2013-01-29
I'm too late now, sorry for the late reply. We lost internet here for a while.

For the benefit of others who may want to know, it is possible to replace the damaged superblock with a backup of the superblock and recover from this kind of file system failure. 
There are lots of backups of the primary superblock and first you need to find out where they are with a command like the following,
```
sudo dumpe2fs /dev/sda1 | grep -i superblock
```

That should return an output something like this, 
> dumpe2fs 1.42 (29-Nov-2011)
  Primary superblock at 0, Group descriptors at 1-4
  Backup superblock at 32768, Group descriptors at 32769-32772
  Backup superblock at 98304, Group descriptors at 98305-98308
  Backup superblock at 163840, Group descriptors at 163841-163844
  Backup superblock at 229376, Group descriptors at 229377-229380
  Backup superblock at 294912, Group descriptors at 294913-294916
  Backup superblock at 819200, Group descriptors at 819201-819204
  Backup superblock at 884736, Group descriptors at 884737-884740
  Backup superblock at 1605632, Group descriptors at 1605633-1605636
  Backup superblock at 2654208, Group descriptors at 2654209-2654212
  Backup superblock at 4096000, Group descriptors at 4096001-4096004
  Backup superblock at 7962624, Group descriptors at 7962625-7962628
  Backup superblock at 11239424, Group descriptors at 11239425-11239428


So you just pick any one of those numbers, for example the first one, 32768, and try restoring that backup to the primary superblock like this,
```
sudo e2fsck -b 32768 /dev/sda1
```
If that doesn't fix it, try again with a different backup.

---

