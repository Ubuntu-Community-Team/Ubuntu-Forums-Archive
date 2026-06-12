---
title: "Upgraded to Ubuntu 16.04.1 - made a mess of my disk ...."
date: 2016-11-26
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2016-11-26
I decided to finally upgrade to 16.04.1 from Ubuntu 14.0.
I did a clean install - but the old version is still in its own partition taking up space.
I do have windows 10 on the hard drive and wanted Ubuntu 16.04 installed next to it. 16.04.1 seems to be working fine, but Grub shows the old 14 system still their in its own partition.

Any suggestions? I just want to be sure I have all disk space reclaimed. Normally I would just wipe the disk and install clean, but I need windows in its own ntfs partition.

Thanks,

---

### Post by oldfred on 2016-11-26
I always do what you have done, so I know that my backup of /home, data, setttings & list of installed apps is complete & I have fully reconfigured new install while old install is still working.

I keep old install as I always use 25GB which is not large with new drives. But have most data in other data partition(s).

You can erase partition. Depending on where it is on drive it may be easy to combined or just about impossible.
Post this, if you have labeled partitions it will show what they are.
sudo parted -l
And this:
       lsblk -o +FSTYPE

---

### Post by michael351 on 2016-11-26
Here are the partitions:

Model: ATA Hitachi HTS54502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  18.3GB  18.3GB  primary   ntfs            diag
 2      18.3GB  18.4GB  105MB   primary   ntfs            boot
 3      18.4GB  104GB   85.3GB  primary   ntfs
 4      104GB   250GB   146GB   extended                  lba
 8      104GB   142GB   38.1GB  logical   ext4
 5      142GB   195GB   52.9GB  logical   ntfs
 6      195GB   248GB   53.1GB  logical   ext4
 7      248GB   250GB   2309MB  logical   linux-swap(v1)




Model: WD Ext HDD 1021 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs


NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT FSTYPE
sda      8:0    0 232.9G  0 disk
&#9500;&#9472;sda1   8:1    0    17G  0 part            ntfs
&#9500;&#9472;sda2   8:2    0   100M  0 part            ntfs
&#9500;&#9472;sda3   8:3    0  79.4G  0 part            ntfs
&#9500;&#9472;sda4   8:4    0     1K  0 part
&#9500;&#9472;sda5   8:5    0  49.3G  0 part            ntfs
&#9500;&#9472;sda6   8:6    0  49.4G  0 part            ext4
&#9500;&#9472;sda7   8:7    0   2.2G  0 part [SWAP]     swap
&#9492;&#9472;sda8   8:8    0  35.5G  0 part /          ext4
sdb      8:16   0   1.8T  0 disk
&#9492;&#9472;sdb1   8:17   0   1.8T  0 part            ntfs


It looks like both sda6 and sda8 contain Ubuntu. I'm not sure which one is the latest version (16), but suspect it is sda8. sda5 looks like windows.

---

### Post by oldfred on 2016-11-26
Windows actually boots from sda2 as that has boot flag. Windows only boots from the primary NTFS partition with the boot flag.

You show sda8 mounted, so if you have booted newer install then sda8 is newer install.

---

### Post by michael351 on 2016-11-27
What about sda6? what is that? (I see it is also ext4) - the older Ubuntu system (14)?

---

### Post by oldos2er on 2016-11-27
Thread moved to *Installation & Upgrades*

---

### Post by oldfred on 2016-11-27
Since sda6 was not mounted, it probably is the older install. 
you probably can compare UUID, fstab and kernels to know which is which for sure.

But you have the NTFS in between the two ext4 partitions which complicates the issue.
NTFS partition do not like being moved. Repairs always required and sometimes do not work.
Before doing anything be sure you have good backups.

---

### Post by michael351 on 2016-11-27
oldfred - Could I just wipe the disk clean - reinstall my windows 10 system (from backup-restore) first and then re-load ubuntu 16 from scratch.
Will this clean up my partitions and free up additional disk space?

---

### Post by oldfred on 2016-11-27
Depends on backups.
But I might just delete sda5 thru 8 and reinstall Ubuntu, particularly if you do not have much configuration effort in Ubuntu or have it backed up.
And make sure to back up the NTFS sda5. NTFS does not like to be moved. And any move with lots of data is slow, but you could move it to start of extended partition if you also have it well backed up. And after move run chkdsk on it.

---

### Post by michael351 on 2016-11-29
Oldfred - would you suggest backup software to do the job correctly. I do have the windows 10 system backed up already, but need to back up the Ubuntu piece. I also have Kodi installed, but have the data files backed up on the network.

---

### Post by oldfred on 2016-11-29
I do not backup Ubuntu itself. With Linux it  is too easy to just reinstall.
I do back my data, /home, some files from /etc and list of installed applications.
But having installed several times with every release, but using LTS as main working install have scripted most updates and install is 10 min, update another 10 min or so. Usually fully configured in about an hour.

Some so like full image backups and use clonezilla.
       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[URL="http://ubuntuforums.org/showthread.php?t=2236636"]http://ubuntuforums.org/showthread.php?t=2236636
[/URL]
 [http://clonezilla.org/](http://clonezilla.org/) 

      
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997) 
    [URL="http://ubuntuforums.org/showthread.php?t=2236636"]
[/URL]

---

### Post by michael351 on 2016-11-30
Clonezilla !! of course - thanks!

One final question - what linux syntax would you use to delete/remove sda5 through 8? I'll then do a re-install of Ubuntu 16.04.1.

Thanks again!

---

### Post by oldfred on 2016-11-30
I have always used gparted. 
Have not used command line since DOS days.

---

