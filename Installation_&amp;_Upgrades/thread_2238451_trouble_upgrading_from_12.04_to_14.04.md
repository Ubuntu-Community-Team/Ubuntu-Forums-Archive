---
title: "trouble upgrading from 12.04 to 14.04"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by glens2 on 2014-08-08
I first updated everything on 12.04 then upgraded through the program. Everything seemed to work except a failure to install a dictionary.
when I restarted it dropped me into the console in initramfs with following messages:

Mount: mounting /dev/loop0 on /root failed: invalid argument
Mount: mounting /dev on /root/dev failed: No such file or directory
..couple of other mount fails off of /root
Target filesystem doesn't have requested /sbin/init

No init found. Try passing init=bootarg

I am at a loss ;-)
I am dual booting with win7 with both operating systems on separate drives and a third drive shared(for email etc)
The grub selection comes up fine and I can select either os but linux only gets as far as initram
The dir structure in the ram fs looks ok, but I don't know where to check for what:-(

Thanks

---

### Post by Bashing-om on 2014-08-08
glens2; HI !

Yeah, a bit perplexing - to say the least:
> 
Mount: mounting /dev/loop0 on /root failed: invalid argument
 loop0 ????/ WUBI ( nope not as a separate hard drive; DVD, nope not if booting from the hard drive ).

Let's look and see what we are working with:
Reset in bios to boot from the liveDVD(USB) .
Boot into "try ubuntu" to a termianl,
post back the outputs - between code tags - of terminal commands :
```

sudo blkid
sudo fdisk -lu
sudo parted -l

```
and we will see about manually mounting the system and have a looksee. Then look about the booting issue.

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by glens2 on 2014-08-08
Bashing-om,

Arkansas huh, I'm from Missouri, just north of the Ozarks

I think the loop0 comes from the drive not being partitioned.
In short I have 4-1T drives
the first is windows
the second is for shared stuff
the third is linux 
the fourth is random

I've been running linux 12.04 on the third for several years.
The problem occurred after upgrading.


```
glen@ubuntu:~$ sudo blkid
[sudo] password for glen: 
/dev/loop0: UUID="3aeb87a9-b001-4bc4-a3b1-cb306b3e4e9c" TYPE="ext3" 
/dev/sda1: LABEL="System Reserved" UUID="D0A02A1AA02A0794" TYPE="ntfs" 
/dev/sda2: LABEL="BootDisk" UUID="E63C41CB3C419787" TYPE="ntfs" 
/dev/sdb1: LABEL="VitutualHosts" UUID="063876DE3876CBE5" TYPE="ntfs" 
/dev/sdd1: LABEL="New Volume" UUID="2E36612B3660F56D" TYPE="ntfs" 
/dev/sdc1: LABEL="Linux" UUID="5640D90640D8EDAD" TYPE="ntfs" 
/dev/sde1: LABEL="KINGSTON" UUID="39BA-B859" TYPE="vfat" 


glen@ubuntu:~$ sudo fdisk -lu
[sudo] password for glen: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfb70a6dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1953521663   976657408    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb06f3ab1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfc5c22a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x314a4be0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sde: 15.6 GB, 15606349824 bytes
116 heads, 52 sectors/track, 5053 cylinders, total 30481152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        8064    30481151    15236544    c  W95 FAT32 (LBA)


glen@ubuntu:~$ sudo parted -l
Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   1000GB  1000GB  primary  ntfs


Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs


Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs


Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs


Model: Kingston DT 101 G2 (scsi)
Disk /dev/sde: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  15.6GB  15.6GB  primary  fat32        boot, lba

```

---

### Post by Bashing-om on 2014-08-09
glens2; Hey,

Yeah, I be a true Arkansas Ridge runner ...

Now I do not want to shock you, just telling you the truth .. you have no partition for ubuntu !
In order to have that partition for ubuntu, it would have a partition type like 'ext4' (default) - but certainly will not be NTFS/FAT formatted !
What in all likely hood you thought of as an ubuntu install is what is termed 'WUBI" an install of ubuntu in a virtual file system residing within Windows .
WUBI, indicated by "/dev/loop0: UUID="3aeb87a9-b001-4bc4-a3b1-cb306b3e4e9c" TYPE="ext3" as known by 'blkid'. Neither 'fdisk' nor 'parted' can see it as it is buried within Windows.

Now for the real bad news, Wubi is no longer supported, and even worse -> I do not know anything further about Wubi and can not advise you on how to access it to retrieve your data.

I trust others can chime in here and offer advise in that respect.

Retrieve your data;
prepare a partition(s) for ubuntu
install ubuntu as a true dual boot .

[INDENT][INDENT]the cold hard truth
[/INDENT][/INDENT]

---

### Post by glens2 on 2014-08-09
well it is not wubi as that was not out when I put this system together, and I have never used it.
I vaguely remember not setting swap or other partitions at the original install. I just put linux on it and it is set so windows does not recognize it.
Figured I would partition it later. :-)
Guess it is later. I was able to get in to it by changing a setting from ro to rw in grub but I have not found the final answer yet. I've found conflicting info in the forums. According to one post the problem is actually in busybox.

---

### Post by hakuna_matata on 2014-08-09
> **glens2 said:**
> I was able to get in to it by changing a setting from ro to rw in grub but I have not found the final answer yet.
After an update of an initramfs-tool script remounting of loop device is not possible. A workaround is to boot with rw instead of ro. So there is no need to remount.

A fix is here: [http://bazaar.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437/revision/281](http://bazaar.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437/revision/281)

If you want to test this fix, you can easily download the fixed revision of the script. Locate this revision to **/etc/initramfs-tools/scripts/local **instead of **/usr/share/initramfs-tools/scripts/local. **This has the advantage that updates don't overwrite this revision. Just update your initramfs and bug will disappear. 

```
sudo wget http://bazaar.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437/download/head:/local-20091205063228-n6wpw4fsn2w1b4pk-42/local -O /etc/initramfs-tools/scripts/local
sudo update-initramfs -u
```

if you want to delete this revision:
```
sudo rm /etc/initramfs-tools/scripts/local
sudo update-initramfs -u
```

---

