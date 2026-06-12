---
title: "No option to install Ubuntu alongside Windows 7"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by deiixmc2 on 2014-04-28
I'm trying to install Ubuntu 14.04 alongside Windows 7 but the option does not appear in the installer. I have two partitions - one is used for boot and is labeled "System Reserved" and the other one is for Windows. I've tried to create a third partition for Ubuntu to no avail. Could somebody point me in the right direction? I'm running the installer from USB.

---

### Post by Bashing-om on 2014-04-28
deiixmc2; Hi ! My Welcome to the forum .

Show us what we are working with;
Post back - between code tags - the outputs of terminal commands (from the liveUSB):
```

sudo fdisk -lu
sudo parted -l

```
Once the partitioning scheme is known we can advise further.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]a little info
[INDENT][INDENT][INDENT]can go a long way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by deiixmc2 on 2014-04-28
Output for sudo fdisk -lu

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xcc3a3c3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   730679295   365236224    7  HPFS/NTFS/exFAT
/dev/sda3       730679296   976773119   123046912   83  Linux

Disk /dev/sdb: 3926 MB, 3926949888 bytes
109 heads, 15 sectors/track, 4691 cylinders, total 7669824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7669823     3834880+   c  W95 FAT32 (LBA)

```


And here is the output for sudo parted -l

```
Model: ATA WDC WD5000AZRX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   374GB  374GB  primary  ntfs
 3      374GB   500GB  126GB  primary  ext4


Model: Kingston DT 100 G2 (scsi)
Disk /dev/sdb: 3927MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  3927MB  3927MB  primary  fat32        boot, lba
```

Thanks in advance.

---

### Post by Bashing-om on 2014-04-28
deiixmc2; Humm;

ubuntu is installed to that 3rd partition:
> 
/dev/sda3       730679296   976773119   123046912   83  [color=green]Linux[/color]

(but, you will not be able to hibernate ubuntu, as there is no provision for a 'swap' partition)

You are not able to boot ? Or to put it another way, what results when you try to boot ?

Maybe we need to install grub (ubuntu's boot manager ) to the MBR of the hard drive ?

[INDENT][INDENT]all in the  process
[/INDENT][/INDENT]

---

### Post by deiixmc2 on 2014-04-29
I haven't installed Ubuntu at all seeing as there is no option to install alongside Windows and I don't know how to use the "Something Else" option to dual-boot

---

### Post by deiixmc2 on 2014-04-29
I fixed it. What I did was run boot repair from my Live USB to install GRUB 2.0, then I went to the terminal and typed in "sudo update-grub". This added Windows 7 to the GRUB list.

---

### Post by Bashing-om on 2014-04-29
deiixmc2; Hey,

That warm feeling of satisfaction with a job well done, nothing else like unto it.

[INDENT][INDENT]you do good work
[/INDENT][/INDENT]

---

