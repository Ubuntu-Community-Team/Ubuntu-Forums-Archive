---
title: "Superblock warning - cannot resize partition"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by kamelie1706 on 2012-12-02
Hello,

I have 3 hard drive with the following partition setup

```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0  59.6G  0 disk 
&#9500;&#9472;sda1   8:1    0  57.2G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   2.5G  0 part [SWAP]
sdb      8:16   0 465.8G  0 disk /media/disk1
sdc      8:32   0 465.8G  0 disk /media/disk2
sr0     11:0    1  1024M  0 rom

```

I have actually one for sdb (sdb1) and one for sdc(sdc1) but they are not shown with the above command "lsblk". Both occupies full capacities of each hard drive.

This is how I mount them
```

UID=290de80e-6f64-4dea-9cd6-704351e250c6 none            swap    sw              0       0
UUID=fe3c9af4-f074-426e-9bf2-a4c8aa55e372 / ext4 errors=remount-ro,user_xattr 0 1
/dev/sdb        /media/disk1    ext4    errors=remount-ro 0       1
/dev/sdc        /media/disk2    ext4    errors=remount-ro 0       1

```

When I use gparted I get the same warning for sdb1 & sdbc1 partition (see attached screenshot)

fdisk -l
```

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c31ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   119851007    59924480   83  Linux
/dev/sda2       119853054   125044735     2595841    5  Extended
/dev/sda5       119853056   125044735     2595840   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

```

I cannot re-size or change sdb1 & sdc1 but both have data I can access normally.

It seems I have not partition for sdb & sdc disk but I can still use them and mount them directly without partition! :confused:

Any idea where to look in order to fix the situation?

Thanks

---

### Post by darkod on 2012-12-02
Why did you start using sdb and sdc without creating a partition table and partition(s) first? Honestly, I have never seen such a case so far.

The only situation I have seen using disks directly (not partitions) is mdadm software raid. It allows to be created from disks or partitions.

I would suggest moving the data somewhere temporarily, and creating one or more partitions on the disks. It's up to you whether you create a single partition taking the whole disk and the filesystem you use on that partition. After that put the data back.

---

### Post by kamelie1706 on 2012-12-02
Hi,

this is what happened ... ubuntu just partitioned my main disk sda during installation but i could start using the 2 others without partitioning.

I will probably follow your advice but need to find the correct command to backup/copy keeping all files information (user rights & permissions included) and buy an usb hardrive to backup. 
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)


I have NAS but as they are not ext4 so I am afraid to lose the user rights (one hard drive contain my backintime directory).

---

### Post by oldfred on 2012-12-02
If you copy to NTFS or other non-Linux formats you will lose ownership & permissions. But if it is just data, not system, you should be able to just reset, unless you have lots of users and  have manually changed permissions.

But if you use any of the compressed backups, that will preserve your settings.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

    I just use rsync but tar will preserve your ownership & permissions.
       Tar backup script:
[https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html)

    
       #If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone
I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
#where $USER should be your login name
# better if both directories & files
       chmod -R a+rwX,go-w /path/to/folder
sudo chmod -R a+rwX,o-w /folder
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

---

### Post by darkod on 2012-12-02
When I was moving my root and /home partition to my new SSD I used from live session:
sudo cp -ax /source /target

The options -ax keep the ownership and permissions. The OS worked just fine after copying with cp -ax without the need to do anything more.

---

### Post by kamelie1706 on 2012-12-02
the only directory I need to be carefull is my backintime directory as it contains many logical & hard links ... any hint for this one? Rest should be fine as they are only data files.

---

