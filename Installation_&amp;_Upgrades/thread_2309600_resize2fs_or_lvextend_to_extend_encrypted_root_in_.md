---
title: "resize2fs or lvextend to extend encrypted root in a (hosted) VM"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2016-01-11
I'm running my mailserver (Ubuntu 10.04 LTS 64 bit server edition) on a VPS and got the people hosting this service to extend the disk do 26GB (from 15)

I have boot root and swap partitions with swap and root encrypted

/dev/xvd already shows the extended size 

```
llist@llmail:~$ sudo fdisk -l

Disk /dev/xvda: 26.8 GB, 26843545600 bytes
255 heads, 63 sectors/track, 3263 cylinders, total 52428800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00027e1c

    Device Boot      Start         End      Blocks   Id  System
/dev/xvda1   *        2048     1075199      536576   83  Linux
/dev/xvda2         1075200    31455231    15190016   8e  Linux LVM
```

```
llist@llmail:~$ sudo parted -l

Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/EncrUbunt-swap_crypt: 998MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system     Flags
 1      0.00B  998MB  998MB  linux-swap(v1)


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/EncrUbunt-EncrUbuntu_crypt: 14.6GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  14.6GB  14.6GB  ext4


Error: /dev/mapper/EncrUbunt-swap: unrecognised disk label                

Error: /dev/mapper/EncrUbunt-EncrUbuntu: unrecognised disk label          

Model: Xen Virtual Block Device (xvd)
Disk /dev/xvda: 26.8GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  551MB   549MB   primary  ext4         boot
 2      551MB   16.1GB  15.6GB  primary               lvm
```

```
llist@llmail:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/EncrUbunt/swap
  LV Name                swap
  VG Name                EncrUbunt
  LV UUID                cU53xe-gBG3-Lgno-1Kfd-pseN-qckN-ZnuBMH
  LV Write Access        read/write
  LV Creation host, time mail, 2014-05-01 22:30:40 +1000
  LV Status              available
  # open                 1
  LV Size                952.00 MiB
  Current LE             238
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/EncrUbunt/EncrUbuntu
  LV Name                EncrUbuntu
  VG Name                EncrUbunt
  LV UUID                XvqLCU-6LMr-AadR-uWrU-HGe8-zWwK-LZwIED
  LV Write Access        read/write
  LV Creation host, time mail, 2014-05-01 22:31:22 +1000
  LV Status              available
  # open                 1
  LV Size                13.55 GiB
  Current LE             3470
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
```

While there seems to be a fair amount of 'HowTos' for this, most seem outdated (or wrong) and none specifically handle extending encrypted roots without dismount.


Do I need to extend /dev/xvda2 with parted and then use resize2fs or can I just extend with lvextend?

Thanks,

Leo

---

### Post by lister171254 on 2016-01-15
The following approach worked for me on a VirtualBox VM running 14.04 LTS server installed for the purpose of trying different approaches.

The VM was created with 9GB for one disk /dev/sda. 

I created 
[LIST]
[*]"/boot" with 200MB
[*]"swap" (encrypted) with 400MB
[*]"/"        (encrypted) with the rest of the space
[/LIST]

I then shut down the VM and extended the storage to 12GN

```
sudo fdisk /dev/sda

Command (m for help): p

Disk /dev/sda: 12.6 GB, 12582912000 bytes
255 heads, 63 sectors/track, 1529 cylinders, total 24576000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d2510

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      391167      194560   83  Linux
/dev/sda2          393214     1368063      487425    5  Extended
/dev/sda3         1368064    18872319     8752128   83  Linux
/dev/sda5          393216     1368063      487424   83  Linux
```

This shows that the disk has 12GB available, but uses less

I then deleted partition 3, which is "/"

```
Command (m for help): d
Partition number (1-5): 3

Command (m for help): p

Disk /dev/sda: 12.6 GB, 12582912000 bytes
255 heads, 63 sectors/track, 1529 cylinders, total 24576000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d2510

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      391167      194560   83  Linux
/dev/sda2          393214     1368063      487425    5  Extended
/dev/sda5          393216     1368063      487424   83  Linux
```

I then created a new partition for with the same start sector as the one I deleted and the (extended) default as the last sector

```
Command (m for help): n
Partition type:
   p   primary (1 primary, 1 extended, 2 free)
   l   logical (numbered from 5)
Select (default p): p
Partition number (1-4, default 3): 
Using default value 3
First sector (391168-24575999, default 391168): 1368064
Last sector, +sectors or +size{K,M,G} (1368064-24575999, default 24575999): 
Using default value 24575999

Command (m for help): p

Disk /dev/sda: 12.6 GB, 12582912000 bytes
255 heads, 63 sectors/track, 1529 cylinders, total 24576000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d2510

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      391167      194560   83  Linux
/dev/sda2          393214     1368063      487425    5  Extended
/dev/sda3         1368064    24575999    11603968   83  Linux
/dev/sda5          393216     1368063      487424   83  Linux
```

Confirming that partition 3 was now extended and the other partitions unaffected I wrote the new partition table

```
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.
```

After a reboot, I can now use resize2fs to extend

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.3G  4.0K  1.3G   1% /dev
tmpfs           257M  468K  257M   1% /run
/dev/dm-0       8.1G  1.7G  6.0G  23% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M  4.0K  5.0M   1% /run/lock
none            1.3G     0  1.3G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda1       180M   80M   87M  48% /boot

sudo resize2fs /dev/dm-0
 
resize2fs 1.42.9 (4-Feb-2014)
Filesystem at /dev/dm-0 is mounted on /; on-line resizing required
old_desc_blocks = 1, new_desc_blocks = 1
The filesystem on /dev/dm-0 is now 2900480 blocks long.

df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.3G  4.0K  1.3G   1% /dev
tmpfs           257M  468K  257M   1% /run
/dev/dm-0        11G  1.7G  8.6G  17% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            1.3G     0  1.3G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda1       180M   80M   87M  48% /boot
```


Credit goes to this guy [https://codesilence.wordpress.com/2013/03/14/live-resizing-of-an-ext4-filesytem-on-linux/](https://codesilence.wordpress.com/2013/03/14/live-resizing-of-an-ext4-filesytem-on-linux/)

---

