---
title: "Lost partition during instalation..."
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by astratow on 2011-02-22
Well... I had fat32 partition and by misclick I selected to mount it as Fat 16 I believe. This is during instalation. Instalator blown up error, I tried with correct details, but there was more and more errores. now I have no acces to the partition, it doesn't show as FAT, just unknown. GPart gave incorrect information I believe. Unless I dont know how to use it... Can anyone help me recover data from this partition? I had a lot of multimedia on there and it is really bad to loose it:(
Thanks a lot in advance!

---

### Post by tommcd on 2011-02-22
Assuming you have installed Ubuntu onto your hard drive properly, boot up Ubuntu and open a terminal and run:
```
sudo fdisk -l
```
and post the output here.
Also (assuming you have installed Ubuntu) did you do a Wubi (inside Windows) Ubuntu install? Or did you do a real install to a dedicated linux partition on your hard drive?

Or, if your Ubuntu install will not boot, then run the Ubuntu live CD and from there post the output of "*sudo fdisk -l*".
You need to provide more info if you want good jelp with this.
Also, if your data is important to you, you should have proper backups for it.
 
And welcome to the Ubuntu forums!

---

### Post by astratow on 2011-02-23
Thank You for welcoming me in forum, greetings to You too. I haven't installed ubuntu via Windows, I didn't know there is possibility to do so. I installed windows just to have a look how things are. Partition exists, but has been recognised as existing but  unformatted. So all Windows suggest is to format thing.  I hope  data are still there and there is possibility to recover them but how? - this is my issue.

---

### Post by astratow on 2011-02-23
I apologise for my incompetence and thank You for quick response. I installed ubuntu on regular ext3 partition. It runs ok, but I am a bit worried to update it, because last time it ended up kernel panic, so I installed it again and during this I have done this misclick, which was incorrect declaration about mounting FAT32 partition (I think I have made it as Fat16).

[I]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       28664   230195385    7  HPFS/NTFS
/dev/sda3           28665       29773     8900041+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5           28665       29772     8899978+   7  HPFS/NTFS
/dev/sda6           29999       30394     3180838+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ac77c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12839   103129236    7  HPFS/NTFS
/dev/sdb2   *       12840      121601   873630734+   f  W95 Ext'd (LBA)
/dev/sdb5           12840       35058   178474086    b  W95 FAT32
/dev/sdb6           35059       60557   204820686    b  W95 FAT32 [/I]<== missing baby[I]
/dev/sdb7           76355       76616     2104483+  82  Linux swap / Solaris
/dev/sdb8           79228      121601   340369123+  83  Linux
/dev/sdb9           63169       73743    84935680    b  W95 FAT32
/dev/sdb10          60558       63168    20971520   83  Linux
/dev/sdb11          73743       76355    20979712   83  Linux
/dev/sdb12          76617       79227    20971520   83  Linux

Partition table entries are not in disk order
[/I]
And yes, I would do back up now, but it is a bit late for that:/
Thanks for Your help in advance

---

### Post by tommcd on 2011-02-23
First, you have 4 linux partitions. Was that intentional? If they are all different installs of Ubuntu then you could just delete the ones that you are not using. If that was intentional and they have data on them or something else then that is fine.

Your partitions on /dev/sdb (your second hard drive) are out of order, but I do not think that is a problem by itself.
So /dev/sdb6 is the FAT32 partition that is missing? See if you can manually mount it like this:
First, create a directory for it:
```
sudo mkdir /media/FAT32
```
Note: you can replace FAT32 in that command with any name you would like for it.
Then try to mount it:
```
sudo mount /dev/sdb6 /media/FAT32
```
Or you could use this to mount it by specifying the file system type:
```
sudo mount -t vfat /dev/sdb6 /media/FAT32
```
If you get errors, then post them here. That partition clearly exists, so you should be able to mount it.

Also post you *etc/fstab* file. Just run in the terminal:
```
cat /etc/fstab
```
and post the output here.

---

### Post by astratow on 2011-02-24
Hi,
[I]~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb12 during installation
UUID=83b1d05c-4db2-4184-b28e-39e5b5f78741 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb8 during installation
UUID=4371d9af-e07d-4f26-b4fd-9f89cb17291f /home           ext3    defaults        0       2
# /windows was on /dev/sdb1 during installation
UUID=E4D84905D848D806 /windows        ntfs    defaults,umask=007,gid=46 0       0
/dev/sdb7       none            swap    sw              0       0[/I]

Attempting to mount gives following results:

[I]sudo mount /dev/sdb6 /media/FAT32
mount: you must specify the filesystem type[/I]

[I]sudo mount -t vfat /dev/sdb6 /media/FAT32
mount: wrong fs type, bad option, bad superblock on /dev/sdb6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]

And after suggested operation:

[I]~$ dmesg | tail
[   18.648077] CPU1 attaching sched-domain:
[   18.648078]  domain 0: span 0-2 level MC
[   18.648080]   groups: 1 2 0
[   18.648084] CPU2 attaching sched-domain:
[   18.648085]  domain 0: span 0-2 level MC
[   18.648087]   groups: 2 0 1
[   24.872031] eth0: no IPv6 routers present
[  140.559741] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  927.232306] FAT: bogus sectors per cluster 0
[  927.232313] VFS: Can't find a valid FAT filesystem on dev sdb6.

[/I]What all that means, I have no idea. Tell me please what would You suggest about  partitioning - You have said it's messy.
Cheers!

---

### Post by dino99 on 2011-02-24
what a mess :( why using this outdated FATxx thing ?

follow this little help:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by tommcd on 2011-02-24
From your /etc/sfstab it looks like you only have 1 Windows partition listed there: /dev/sdb1. Are you able to mount any of the others?
> **astratow said:**
> 
Attempting to mount gives following results:

[I]sudo mount -t vfat /dev/sdb6 /media/FAT32
mount: wrong fs type, bad option, bad superblock on /dev/sdb6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]

And after suggested operation:

[I]~$ dmesg | tail

[  927.232313] VFS: Can't find a valid FAT filesystem on dev/sdb6.

From your attempt to mount /dev/sdb6, and the output of *dmesg*, it looks like the file system on /dev/sdb6 may be corrupted. Are you able to access the data on that partition from Windows?

To elaborate on what **dino99** said, all you really need for Ubuntu is 3 partitions:
root: (where your operating system lives)
swap: (this is a partition that can serve to swap out programs from memory if you run out of memory. This is analogous to "virtual memory" in Windows).
home: This is where your data and user specific configuration files are kept.

I don't think the fact that your partitions are out of order on /dev/sdb is a problem by itself.
Your /dev/sda3 extended partition does not end on a cylinder boundary as per your output from *fdisk*. If that is not causing you a problem I would not worry about.
The only way fix your partition table would be to repartition the drive(s).

---

### Post by astratow on 2011-03-02
Hi,
I revived partition using **testdisk**. It was a bit tricky, because they are called different than in other programs (testdisk describes  partition in cylinders). 
Thank You all!

---

