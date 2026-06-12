---
title: "GRUB dual boot no more access to Ubuntu"
date: 2020-08-08
forum: Installation &amp; Upgrades
---

### Post by ortollj on 2020-08-08
Hi
I have encountered a problem with the dual boot since last night, I can no longer access Ubuntu 18.04 through GRUB,
on the other hand I always access W10.

```
/dev/sda7 contains a file system with error check forced

Inodes that were part of a corrupted orphan linked list found.

fsck exited with status code 4

```

do I have any hope of getting my Ubuntu back? what could I try to repair ?
in the meantime I try to install Ubuntu  in W10

---

### Post by CelticWarrior on 2020-08-08
The error message indicates the system partition is corrupt and needs file system error correction.

---

### Post by ortollj on 2020-08-08
is it possible to attempt a repair booting on usb key ?

---

### Post by CelticWarrior on 2020-08-08
> **ortollj said:**
> is it possible to attempt a repair booting on usb key ?

Yes, actually it must be.

---

### Post by ortollj on 2020-08-08
I have booted on my usb key, but I do not see repair option in installation tool, what could I do ?
because I have files in old installation that I would like to recover, do you think it will be possible ?

---

### Post by ortollj on 2020-08-08
oh its ok I can recover my files, I just have to go to my ubuntu partition disk, and go to my user name, and I can see all my files in documents  ;-)
I will copy all on my usb key !

---

### Post by pbear42 on 2020-08-08
> **ortollj said:**
> I have booted on my usb key, but I do not see repair option in installation tool, what could I do ?
You run *fsck* in Terminal.  The form of command is sudo fsck -yv /dev/sdxn, where x is the device letter and n the partition number.

By the way, you also can run *fsck* from Advanced Options > Recovery Mode.  It's one of the choices on the menu.

---

### Post by ortollj on 2020-08-08
oh its ok I can recover my files, I just have to go to my ubuntu partition disk, and go to my user name, and I can see all my files in documents  ;-)
I will copy all on my usb key !

---

### Post by ortollj on 2020-08-08
all my files have been recovered except 6 or 7 pdf files ;-)
I'm gonna try to run fsck with the options you recomand

---

### Post by ortollj on 2020-08-08
I got this:

```
ubuntu@ubuntu:~$ sudo fsck -yv /dev/sda7
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sda7 is mounted.
e2fsck: Cannot continue, aborting.
ubuntu@ubuntu:~$
```

I think I will try Ubuntu inside W10, I almost finished installing it, I still have the Ubuntu_desktop part to install and  test, there is something fishy about GRUB !

---

### Post by pbear42 on 2020-08-08
The error message is clear enough, and wouldn't have come up if you had done as suggested in the first place.  Hope it works out.  Good luck.

---

### Post by ajgreeny on 2020-08-08
Boot again to your live USB system and from that check the partition naming is still as you have seen before with ```
sudo parted -l
``` and if the root filesystem is still the same, run your command ```
sudo fsck -yv /dev/sda7
``` from there; it should work fine.

---

### Post by ortollj on 2020-08-09
ok ajgreeny I did what you recomand :

```
ubuntu@ubuntu:~$ sudo parted -l

 Model: ATA TOSHIBA MQ01ABD1 (scsi)
 Disk /dev/sda: 1000GB
 Sector size (logical/physical): 512B/512B
 Partition Table: gpt
 Disk Flags:  
 
 
 Number  Start   End     Size    File system  Name                  Flags
  1      1049kB  1075MB  1074MB  ntfs         Basic data partition  hidden, diag
  2      1075MB  1180MB  105MB   fat32        Basic data partition  boot, esp
  3      1180MB  1314MB  134MB   ntfs         Basic data partition  msftres
  4      1314MB  882GB   881GB   ntfs         Basic data partition  msftdata
  7      882GB   987GB   105GB   ext4
  5      987GB   988GB   1060MB  ntfs                               hidden, diag
  6      988GB   1000GB  12.2GB  ntfs         Basic data partition  hidden, diag
 
 
 
 
 Model: SanDisk Ultra (scsi)
 Disk /dev/sdb: 61.5GB
 Sector size (logical/physical): 512B/512B
 Partition Table: msdos
 Disk Flags:  
 
 
 Number  Start   End     Size    Type     File system  Flags
  1      16.4kB  61.5GB  61.5GB  primary  fat32        boot, lba
 
 
 
 
 
 
 
 
 
 
 ubuntu@ubuntu:~$ sudo fsck -yv /dev/sda2
 fsck from util-linux 2.31.1
 fsck.fat 4.1 (2017-01-24)
 Checking we can access the last sector of the filesystem
 Boot sector contents:
 System ID "MSDOS5.0"
 Media byte 0xf8 (hard disk)
        512 bytes per logical sector
       1024 bytes per cluster
       6654 reserved sectors
 First FAT starts at byte 3406848 (sector 6654)
          2 FATs, 32 bit entries
     393728 bytes per FAT (= 769 sectors)
 Root directory start at cluster 2 (arbitrary size)
 Data area starts at byte 4194304 (sector 8192)
      98304 data clusters (100663296 bytes)
 63 sectors/track, 255 heads
    2099200 hidden sectors
     204800 sectors total
 Reclaiming unconnected clusters.
 Checking free cluster summary.
 /dev/sda2: 379 files, 59477/98304 clusters
  
```
no I m gonna try to reboot after removing my usb key, and I will tell you the result

---

### Post by ortollj on 2020-08-09
its ok now !!!!
thanks to all. I need to redo  the fsck command in the menu I got when the pc cant boot on Ubuntu
I did it 3 times first in my Ubuntu terminal and twice in the boot menu. the first time in the boot menu after typing reboot I saw a Ubuntu violet screen and it disappeared and it comes back to reboot menu
so I did it again and it repair a lot of things, I took a photo of the screen but I m not allowed to post an image here.I did the command fsck -yv /dev/sda7 in boot mod.

here in a google doc I put the photo:[https://docs.google.com/document/d/1A6c_ygPvHqIVA87ttyGxyGh6yU8KnYmmEPP8IySTcBk/edit?usp=sharing](https://docs.google.com/document/d/1A6c_ygPvHqIVA87ttyGxyGh6yU8KnYmmEPP8IySTcBk/edit?usp=sharing)

---

### Post by dragonfly41 on 2020-08-09
That image is difficult to read (at least for me).
I believe that there might be a log placed here ..
[B]/run/initramfs/fsck.log


[/B]

---

### Post by ortollj on 2020-08-09
@dragonfly41, you can read the photo if you choose 200 % in google doc

under /run/initramfs thre are only 2 files fsck-root and fsck.log .
fsck-root is empty and below what is in fsck.log quasi empty !:

[B]Log of fsck -C -a -T -t ext4 /dev/sda7 
Sun Aug  9 06:09:07 2020

/dev/sda7: clean, 802097/6406144 files, 13861975/25600000 blocks

Sun Aug  9 06:09:07 2020
----------------[/B]

---

