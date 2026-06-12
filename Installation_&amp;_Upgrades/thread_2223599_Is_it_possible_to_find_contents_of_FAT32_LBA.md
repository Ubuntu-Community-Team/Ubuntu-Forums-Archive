---
title: "Is it possible to find contents of FAT32 LBA"
date: 2014-05-11
forum: Installation &amp; Upgrades
---

### Post by Yusuf_Yildiz on 2014-05-11
Hey there guys, I've been trying to get some files out of my old partition that I messed up when creating one for Ubuntu. I'm wondering if there was a way that I could access some of my documents using ubuntu seeing that I can't boot into Windows anymore. Thanks guys.

---

### Post by sudodus on 2014-05-12
Please describe your computer as detailed as possible :-)

Also please run these commands in a terminal window, copy and past the output into a reply window

```
sudo parted -l
```

```
sudo blkid
```

```
df
```

Click on the read button 'Go Advanced', mark the output text and click on the # icon at the top of the editing window to get them within code tags.

---

### Post by Yusuf_Yildiz on 2014-05-12
How is this?

```
yildiz@Yildiz:~$ sudo parted -l[sudo] password for yildiz: 
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  512MB   511MB   linux-swap(v1)
 2      512MB   20.5GB  20.0GB  ext4
 3      20.5GB  60.5GB  40.0GB  ext4
 4      60.5GB  60.8GB  256MB   fat32                 boot




Model:  USB Flash Memory (scsi)
Disk /dev/sdb: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba




yildiz@Yildiz:~$ sudo blkid
/dev/sda1: UUID="e952b9fb-e383-4c70-b0b3-d7f4c8cbeb22" TYPE="swap" 
/dev/sda2: UUID="deee3bca-170d-44e5-8e92-e539240c5278" TYPE="ext4" 
/dev/sda3: UUID="22f6a7cf-d3f7-4d21-90d9-5a99dd5cbccb" TYPE="ext4" 
/dev/sda4: UUID="82A4-2771" TYPE="vfat" 
/dev/sdb1: UUID="7754-4EE7" TYPE="vfat" 
yildiz@Yildiz:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda2       19091584 5139760  12958956  29% /
none                   4       0         4   0% /sys/fs/cgroup
udev             3759724       8   3759716   1% /dev
tmpfs             754096    1408    752688   1% /run
none                5120       0      5120   0% /run/lock
none             3770460     324   3770136   1% /run/shm
none              102400      36    102364   1% /run/user
/dev/sda4         245996    3427    242570   2% /boot/efi
/dev/sda3       38317716 6652900  29695308  19% /home
/dev/sdb1       15228376  280568  14947808   2% /media/yildiz/7754-4EE71



```

---

### Post by sudodus on 2014-05-12
It does not look good. You have overwritten the Windows partition, which should have an NTFS file system.

There are a couple of methods that *might* save your files, but chances are rather small, that you can restore everything.

1. Try Testdisk that can restore file systems in some cases.

2. Try PhotoRec that can recover most file types directly from the data on the drive surface with a file system.

But what is overwritten by your installation cannot be recovered.

See this link [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by Yusuf_Yildiz on 2014-05-12
Thanks sudodus, I appreciate your help!

---

### Post by Yusuf_Yildiz on 2014-05-13
Do you know how I can get to my recovery partitions? I've been looking everywhere but I think that when overwriting over the windows partition the recover partition was also overwritten... 
Thanks, I appreciate any help!

---

### Post by sudodus on 2014-05-13
The entries in the partition table are overwritten. If the recovery partitions were near the head end of the drive, their data were probably overwritten by data belonging to Ubuntu. If they were  near the tail end of the drive, the data might have survived, but is hard to recover completely.

You own private data is unique, and you might be able to recover some of it with PhotoRec.

The Windows recovery partitions contain standard data, that you can get, if you buy a recovery disk (and use the licence that belongs to the computer). It is much cheaper than to buy a new Windows disk and licence.

---

