---
title: "Windows 7 Ubuntu Dual Boot Installation with existing mounting partitions"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by JYzeeeJ on 2013-12-08
So I am trying to install ubuntu on my work pc and it says the following:

```
The installer has detected that the following disks have mounted partitions:

/dev/sda, /dev/sdb

Do you want the installer to try to unmount the partitions on these disks before continuing? If you leave them mounted, you will not be able to create, delete, or resize partitions on these disks, but you may be able to install to existing partitions there
```

What is my best course of action?

---

### Post by oldfred on 2013-12-08
I am not sure you should be getting mounted partitions. Is Windows hibernated, is system RAID or some other special configuration?
Post this from the live mode installer.

sudo parted -l
df -h

I do that that same message, but I install from one hard drive to another and the partition with the ISO that I loopmount is mounted. But since I an not doing anything to that drive I do ignore message.

---

### Post by JYzeeeJ on 2014-10-24
No RAID drives. This is the output I get:

```

ubuntu@ub[FONT=arial][/FONT]untu:~$ sudo parted -l
Model: ATA V4-CT256V4SSD2 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  840MB  839MB   primary  ntfs         boot
 2      840MB   249GB  248GB   primary  ntfs
 3      249GB   256GB  6708MB  primary  ntfs
 4      256GB   256GB  110MB   primary  fat32        diag


Model: ATA WDC WD10EZEX-00R (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs


Model: Chipsbnk UDisk (scsi)
Disk /dev/sdc: 1993MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  1993MB  1993MB  primary  fat32        boot, lba

```

```

ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow             59M   30M   26M  55% /
udev            7.8G  4.0K  7.8G   1% /dev
tmpfs           1.6G  1.3M  1.6G   1% /run
/dev/sdc1       1.9G  1.1G  854M  55% /cdrom
/dev/loop0      939M  939M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           7.9G  1.1M  7.9G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            7.9G   76K  7.9G   1% /run/shm
none            100M   60K  100M   1% /run/user
/dev/loop1       59M   30M   26M  55% /media/ubuntu/casper-rw

```

---

### Post by JYzeeeJ on 2014-10-24
[FONT=arial][COLOR=#333333]My current plan:[/COLOR]
[/FONT]
[LIST]
[*][FONT=arial]Create new partitions on [COLOR=#000000]/dev/sda[/COLOR] for Linux so that I have the following:[/FONT]
[LIST]
[*][FONT=arial]SYSTEM: 800MB NTFS[/FONT]
[*][FONT=arial]WINDOWS: 100GB NTFS[/FONT]
[*][FONT=arial]LINUX: 120GB EXT4[/FONT]
[*][FONT=arial]LINUX SWAP: 16GB EXT4[/FONT]
[/LIST]
[/LIST]

[FONT=arial][COLOR=#333333]This is all new to me, so I have some questions:
[/COLOR]
[/FONT]
[LIST=1]
[*][FONT=arial]Do you think the above partitions are suitable?[/FONT]
[*][FONT=arial]Is the install error shown because there are already multiple partitions on [COLOR=#000000]/dev/sda[/COLOR]?[/FONT]
[*][FONT=arial]I will be transferring my projects to Linux so I should free up room on WINDOWS, will I be able to update the partitions in the future without too much hassle?[/FONT]
[*][FONT=arial]I read that the LINUX SWAP partition should match the RAM - is that correct?[/FONT]
[/LIST]

---

### Post by oldfred on 2014-10-24
You do have the 4 primary partition limit issue.

Your partition plan is ok, but I prefer smaller system partitions for both Windows & Linux and larger data partition(s). I think what you show for Windows system is just its Boot partition which normally is 100MB. Then you have the main Windows or c: "drive". I would then add another NTFS for data only.

Only  if hibernating would you need swap equal to RAM in MiB, not MB. If you have 16GB, then you will not use swap at all. I might have 2 or 3GB just to have some. My 4GB RAM system has not used swap, but it does depend on how much you load into RAM at once. Linux does cache activity so RAM use may grow, but anything not recently used would be released for newer program you start to run. 

Is sdb internal or external? If Internal, I would consider installing Ubuntu to that drive.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

    
Be sure to fully backup Windows and make a Windows repair CD or flash drive. Most Windows repairs must be done from Windows repair tools.

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

All Linux and your data partitions can be logical partitions. Windows only requires a primary NTFS partition with the boot flag to boot.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by JYzeeeJ on 2014-10-24
> **oldfred said:**
> You do have the 4 primary partition limit issue.

If Windows lets me I am going to merge partitions #3 and #4 into the #2

> **oldfred said:**
> Is sdb internal or external? If Internal, I would consider installing Ubuntu to that drive.

It is internal but a very slow drive so I just use it as backup.

Thanks for the info and links - just reading through them now to decide how to partition the hard disks.

---

