---
title: "Persistence not working"
date: 2016-02-20
forum: MINT
---

### Post by P.ap G on 2016-02-20
hi.
I am using Mint 17.2 Mate.
When I set up persistence all SEEMS well, the FAT32 partition has grown from
1.7Gb to 6.5 ,and there is a casper-rw file , but when I boot up there is no persistence.Has anyone any ideas ?

Thanks in anticipation

---

### Post by howefield on 2016-02-20
Moved to the "*MINT*" forum.

---

### Post by yancek on 2016-02-20
You can't have a file of any type larger than 4GB on a FAT32 filesystem.  You need to shrink the first partition on which you have the Live CD to just a little larger than the iso files.  You then need to create another partition with a Linux filesystem and label it casper-rw.  Details on the process at the link below starting at creating the casper-rw filesystem.  Read the rest of the page before beginning.

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

---

### Post by sudodus on 2016-02-21
- How did you create the live USB drive?

- How did you set up the persistence?

Please post the output of the following commands, when booted from the live USB drive

```
df -h
sudo parted -ls
sudo lsblk -fm
```

-o-

Maybe you can try with [mkusb](https://help.ubuntu.com/community/mkusb), which works with Ubuntu and Debian Jessie and distros based on them.

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by P.ap G on 2016-02-21
Hi
yancek and sudodus.
I created the usb from another usb(live) using gparted and Startup Disk Creator.
I made a FAT32 partition on the whole drive 8GB,which I realise is not a true 8Gb,gave it a boot flag.
I then opened Startup Disk Creator and selected the maximum 4 GB for persistence.S D C went through 
all its procedures including writing persistence.My apology...the final size was not 6.5Gb as I stated ,but as you can see 5.6 !
The results were:

peter@peter-Lenovo-G580 ~ $ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            2.9G   12K  2.9G   1% /dev
tmpfs           582M  1.5M  580M   1% /run
/dev/sda6       465G   30G  411G   7% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M  4.0K  5.0M   1% /run/lock
none            2.9G  344K  2.9G   1% /run/shm
none            100M   64K  100M   1% /run/user
/dev/sdc1       7.5G  5.6G  1.9G  76% /media/peter/6D68-20CE
peter@peter-Lenovo-G580 ~ $ sudo parted -ls
[sudo] password for peter: 
Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  231GB  231GB   primary   ext4            boot
 2      231GB   750GB  519GB   extended
 6      231GB   738GB  507GB   logical   ext4
 5      738GB   750GB  12.6GB  logical   linux-swap(v1)


Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdc: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8004MB  8003MB  primary  fat32        boot


peter@peter-Lenovo-G580 ~ $ sudo lsblk 
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 698.7G  0 disk 
&#9500;&#9472;sda1   8:1    0 215.2G  0 part 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0  11.7G  0 part [SWAP]
&#9492;&#9472;sda6   8:6    0 471.8G  0 part /
sdc      8:32   1   7.5G  0 disk 
&#9492;&#9472;sdc1   8:33   1   7.5G  0 part /media/peter/6D68-20CE
sr0     11:0    1  1024M  0 rom 
 
peter@peter-Lenovo-G580 ~ $ cd /media/peter/6D68-20CE/
peter@peter-Lenovo-G580 /media/peter/6D68-20CE $ lsa
0200 total 4193384
0700 drwx------  10 peter peter       4096 Jan  1  1970 .
0750 drwxr-x---+  3 root  root        4096 Feb 21 19:19 ..
0700 drwx------   3 peter peter       4096 Feb 18 13:30 boot
0700 drwx------   2 peter peter       4096 Feb 18 13:37 casper
0644 -rw-r--r--   1 peter peter 4293918720 Feb 18 13:56 casper-rw
0700 drwx------   2 peter peter       4096 Feb 18 13:30 .disk
0700 drwx------   3 peter peter       4096 Feb 18 13:37 dists
0700 drwx------   3 peter peter       4096 Feb 18 13:37 EFI
0444 -r--r--r--   1 peter peter      32768 Feb 18 13:37 ldlinux.sys
0644 -rw-r--r--   1 peter peter      24215 Feb 18 13:30 MD5SUMS
0700 drwx------   5 peter peter       4096 Feb 18 13:37 pool
0700 drwx------   2 peter peter       4096 Feb 18 13:37 preseed
0644 -rw-r--r--   1 peter peter        224 Feb 18 13:30 README.diskdefines
0700 drwx------   2 peter peter       8192 Feb 18 13:37 syslinux
peter@peter-Lenovo-G580 /media/peter/6D68-20CE $

---

### Post by yancek on 2016-02-21
The output you posted in your last post shows only one partition (sdc1) on the 8GB flash drive so all you have is a casper-rw file which cannot be larger than 4GB.  You need to create a second partition for casper-rw as explained in the link I posted earlier.

---

### Post by P.ap G on 2016-02-21
But shouldn't have Startup Disk Creator handled that ?

---

### Post by sudodus on 2016-02-21
That version of the Ubuntu Startup Disk Creator *should* handle that for Ubuntu ;-) I'm not sure about Linux Mint, which is another operating system (based on Ubuntu, but different in some ways under the hood).

-o-

It is easier to read the output for terminal commands, if you put it within [noparse]```
tags
```[/noparse]

```
peter@peter-Lenovo-G580 ~ $ df -h
Filesystem Size Used Avail Use% Mounted on
udev 2.9G 12K 2.9G 1% /dev
tmpfs 582M 1.5M 580M 1% /run
[COLOR="#FF0000"]/dev/sda6 465G 30G 411G 7% /[/COLOR]
none 4.0K 0 4.0K 0% /sys/fs/cgroup
none 5.0M 4.0K 5.0M 1% /run/lock
none 2.9G 344K 2.9G 1% /run/shm
none 100M 64K 100M 1% /run/user
[COLOR="#0000CD"]/dev/sdc1 7.5G 5.6G 1.9G 76% /media/peter/6D68-20CE[/COLOR]
```

The red line indicates that you have booted from the internal drive. Please post the output of ```
df -h
``` ***when booted live from the USB pendrive***. That will indicate if the persistence is working or not.

If it is not working I suggest that you try with the ***mkusb*** method instead, because it can create a ***partition*** for persistence automatically, and use all remaining drive space if you wish, 100%, or part of it (for example 50%) and let the rest of it be available for exchange with computers running Windows.

---

### Post by P.ap G on 2016-02-23
I got this when I was live and copied it to my hard drive:

```

mint@mint ~ $ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            2.9G   65M  2.8G   3% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           582M  1.5M  580M   1% /run
/dev/sdb1       7.5G  5.6G  1.9G  76% /cdrom
/dev/loop0      1.6G  1.6G     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.9G  4.0K  2.9G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            2.9G   76K  2.9G   1% /run/shm
none            100M   36K  100M   1% /run/user
mint@mint ~ $ 

```

This what I got from an old live distro which does work ! It looks very similar.

> 
mint@mint ~ $ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            2.5G  606M  1.7G  26% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           592M  1.3M  590M   1% /run
/dev/sdb1       3.8G  3.7G  110M  98% /cdrom
/dev/loop0      1.2G  1.2G     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.9G   12K  2.9G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            2.9G   80K  2.9G   1% /run/shm
none            100M   16K  100M   1% /run/user
mint@mint ~ $ This is an old 32 bit mint


---

### Post by sudodus on 2016-02-23
I agree that the two outputs look very similar. I don't know the details for Linux Mint and the Startup Disk Creator, but I have tested mkusb with Linux Mint 17 (I don't remember which point version), and it worked for me, so maybe you can try with [mkusb](https://help.ubuntu.com/community/mkusb), which works with Ubuntu and Debian Jessie and distros based on them. See the following link

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

You start by installing mkusb from a PPA

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

---

