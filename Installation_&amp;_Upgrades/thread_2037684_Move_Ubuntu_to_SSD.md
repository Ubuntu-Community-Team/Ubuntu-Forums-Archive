---
title: "Move Ubuntu to SSD"
date: 2012-08-05
forum: Installation &amp; Upgrades
---

### Post by crova on 2012-08-05
Hi all!
I currently have Ubuntu 12.04 installed on a 500GB HD and a SSD with Windows 7.
The configuration is the following:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8a895078

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   125954047    62976000   83  Linux
/dev/sda2       749969408   976769023   113399808    7  HPFS/NTFS/exFAT
/dev/sda3       125954048   127002623      524288   82  Linux swap / Solaris
/dev/sda4       127002624   336717823   104857600   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 115.0 GB, 115033153536 bytes
255 heads, 63 sectors/track, 13985 cylinders, total 224674128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ff8ccdb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   224671743   112334848    7  HPFS/NTFS/exFAT

```

Id est, I have 
- a 64GB partition for / ( sda1)
- 537MB for swap ( sda3 )
- 107GB for /home ( sda4 )

Now, what I want to do is partition the SSD for ubuntu and windows and move the existing Ubuntu to the SSD.
How can I do this?? I need to reinstall completely Ubuntu on the SSD or can I move in some way, with clonezilla or something like this?? 
Thanks in advance for the answers :)

---

### Post by darkod on 2012-08-05
You can copy the root partition, I would say something like FS Archiver is better than clonezilla. For clonezilla the destination partition must be same or bigger than the source partition, and in your case going from hdd to ssd you need to use smaller partition.

In any case you need to do a very good math.
How much space do you need for win7? In other words, how much of the ssd can you spare for ubuntu?

Do you plan to move only root on the ssd or also small part of home (because whole home wouldn't fit anyway)?

PS. Also, why do you have such a large part of the hdd not used? Look at the space between the end of sda4 and the start of sda2. Basically like half of the hdd is not used.

---

### Post by crova on 2012-08-05
> **darkod said:**
> You can copy the root partition, I would say something like FS Archiver is better than clonezilla. For clonezilla the destination partition must be same or bigger than the source partition, and in your case going from hdd to ssd you need to use smaller partition.

In any case you need to do a very good math.
How much space do you need for win7? In other words, how much of the ssd can you spare for ubuntu?

Do you plan to move only root on the ssd or also small part of home (because whole home wouldn't fit anyway)?

PS. Also, why do you have such a large part of the hdd not used? Look at the space between the end of sda4 and the start of sda2. Basically like half of the hdd is not used.

First of all thank you :)
So..
 I was thinking of moving only root and leave home on the HDD for any other file etc
 Or do you suggest something different?
Also concerning the space ,Ubuntu is my primary OS so win 7/8 will have less space (the ssd is 115 so maybe 70 Ubuntu and remaining for win..I accept suggestions also here :) ).

The large not used space was another partition I used under windows 7 for holding virtual machines and any other program not needed in the ssd,but now is unused because I formatted the drive some time ago to make partitions for Ubuntu. But I never recreated that partition ^^

---

### Post by oldfred on 2012-08-05
How full is your / (root) sda1 partition? And how full is your Windows on sdb1? Windows NTFS really likes 30% free space.

I install Ubuntu in a 25GB / partition with all my data on a rotating drive. I include /home in / but only the hidden user setting and no data either the data folders like Documents, Music, etc nor some of the hidden folders that are data like the Firefox & Thunderbird profiles. I multi-boot so I want to be able to mount the same data in every install.

I prefer clean installs as it housecleans and makes a working install without some futzing. If you copy install it has UUIDs and you have to edit fstab & reinstall grub anyway. If you image copy you have to change UUID of partition as well.

If you clean install all the UUIDs will be ok, you will have all your old settings as you are using the same /home and if you have a few things in / that you need you can still copy them over as you still have your old install.

Either way backup first & houseclean:
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

I might keep old install on 500GB drive also. Some food for thought:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by crova on 2012-08-05
> **oldfred said:**
> How full is your / (root) sda1 partition? And how full is your Windows on sdb1? Windows NTFS really likes 30% free space.

I install Ubuntu in a 25GB / partition with all my data on a rotating drive. I include /home in / but only the hidden user setting and no data either the data folders like Documents, Music, etc nor some of the hidden folders that are data like the Firefox & Thunderbird profiles. I multi-boot so I want to be able to mount the same data in every install.

I prefer clean installs as it housecleans and makes a working install without some futzing. If you copy install it has UUIDs and you have to edit fstab & reinstall grub anyway. If you image copy you have to change UUID of partition as well.

If you clean install all the UUIDs will be ok, you will have all your old settings as you are using the same /home and if you have a few things in / that you need you can still copy them over as you still have your old install.

Either way backup first & houseclean:
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

I might keep old install on 500GB drive also. Some food for thought:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

The disk usage is:
```

/dev/sda1      ext4       60G   30G   28G  52% /
/dev/sda4      ext4      100G   42G   54G  44% /home
/dev/sdb1      fuseblk   108G   50G   58G  47% /media/0622F7DA22F7CCA5
Filesystem     Type      Size  Used Avail Use% Mounted on

```

So you suggest a fresh install? 
I don't want to reinstall all the software on Ubuntu (that's why I wanted to use a cloning app)..there is a way to do that automagically?? :D

---

### Post by oldfred on 2012-08-05
I regularly use this, but have found after multiple new versions that I am still installing obsolete applications. For example I was still reinstalling python2.5. Now they have obsoleted OpenOffice and are using LO so you do not want both normally. I include a new copy to the package list with every rsync backup of my /home.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

My backup is to make sure I have everything I need to reinstall. This works for me on several upgrades but is only a desktop home system not a server or system that needs a lot of detailed backup.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by crova on 2012-08-07
There is a problem (in terms of performance too) if I install Ubuntu on ssd, remaining home on the HDD?

---

### Post by oldfred on 2012-08-07
That is part of the reason I split /home into user settings and data. The data will be somewhat slower but you do not use it that much. It primarily is system that needs to be on SSD. Of course if you have a large enough SSD then you want as much as possible on SSD.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by modprob on 2012-08-23
fred thanks.
the dpkg  trick works

also other tell of aptoncd
way 2 , no cloud.

thanks again. ! saved tons of work.
then the home restore... last.

---

