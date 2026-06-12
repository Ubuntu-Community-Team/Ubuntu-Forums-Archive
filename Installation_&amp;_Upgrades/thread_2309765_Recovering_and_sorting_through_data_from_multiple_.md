---
title: "Recovering and sorting through data from multiple partitions, some encrypted?"
date: 2016-01-13
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2016-01-13
As much as I love the performance of my 250 GB SSD, it simply is not enough space, especially when dual booting. Due to this yesterday I installed an old 2TB HDD, and an even older 320GB HDD, both of which I would like to go through and backup anything important from to a third temporarily installed 1TB HDD. I will only back up some of the data, and the 2TB is not fully in use so the 1TB HDD should be enough for backup. I would then like to format both the 2TB and 320GB and use them for storage.

At least one of the two HDDs were used to dual boot Windows and *buntu in the past, and at least one of the partitions on one of the disks is encrypted and I have passwords and passphrases recorded. There are multiple partitions to work with here, and I would like to start with the 2TB drive and systematically access and go through each partition, decrypting where necessary, backing up what I need, before deleting each partition and moving onto the next. I want to be able to view the drives and partitions so I can get a sense of the hierarchy to go through them. I have several partitions visible on the launcher with disk icons but when I click on any I receive this error:

```
Error mounting /dev/sdb7 at /media/abcd/OLD DUMP: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb7" "/media/abcd/OLD DUMP"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb7': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```

As a precaution I logged into Windows 10 and made sure I shut it down fully rather than using hibernate or sleep, but this made no difference. I also appreciate this error may have something to do with an old Windows or Ubuntu install on one of the HDDs, but I think when I initially booted into Ubuntu yesterday after physically installing the HDDs I was able to access at least some of the partitions. Also strangely, although yesterday using GParted I created a GPT partition table on the 1TB drive (which I want to use as a temporary backup), formatted it to NTFS (just so both OS can access it easily), labelled it BACKUP, and I was able to access it - today I receive similar errors:

```
Error mounting /dev/sda1 at /media/abcd/BACKUP: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda1" "/media/abcd/BACKUP"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```
 
 ```
abcd@roadrunner:~$ sudo mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda1" "/media/abcd/BACKUP"

 The disk contains an unclean file system (0, 0).
 Metadata kept in Windows cache, refused to mount.
 Failed to mount '/dev/sda1': Operation not permitted
 The NTFS partition is in an unsafe state. Please resume and shutdown
 Windows fully (no hibernation or fast restarting), or mount the volume
 read-only with the 'ro' mount option.
 abcd@roadrunner:~$ sudo mount -ro "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda1" "/media/abcd/BACKUP"
 ntfs-3g-mount: bad mount point /media/abcd/BACKUP: No such file or directory
```

I am able to access these partitions if I log into Windows but I would like to do this through Ubuntu if I can.

```
abcd@roadrunner:~$ sudo fdisk -l | grep /dev/sd
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
/dev/sda1   2048 1953523711 1953521664 931.5G Microsoft basic data
Disk /dev/sdb: 298.1 GiB, 320072933376 bytes, 625142448 sectors
/dev/sdb1  *           63 116840744 116840682  55.7G  7 HPFS/NTFS/exFAT
/dev/sdb3       116828160 625137344 508309185 242.4G  f W95 Ext'd (LBA)
/dev/sdb5       116830208 148285407  31455200    15G 83 Linux
/dev/sdb6       148287488 177184767  28897280  13.8G 83 Linux
/dev/sdb7       177186816 616749055 439562240 209.6G  7 HPFS/NTFS/exFAT
/dev/sdb8       616751104 625135615   8384512     4G 82 Linux swap / Solaris
Disk /dev/sdc: 232.9 GiB, 250059350016 bytes, 488397168 sectors
[I]/dev/sdc1       2048   2099199   2097152     1G EFI System
/dev/sdc2    2099200 211814399 209715200   100G Microsoft basic data
/dev/sdc3  211814400 457676799 245862400 117.2G Linux filesystem
/dev/sdc4  457676800 488396799  30720000  14.7G Linux filesystem[/I]
Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
/dev/sdd1        2048 3907028991 3907026944  1.8T  7 HPFS/NTFS/exFAT
```

sdc is the SSD. If it matters when I open GParted it tells me 'Libparted bug found! Cannot have overlapping partitions', and this not an error GParted output before I installed the three HDDs yesterday.

- Please advise if pasting the output of any other command would help, and where to start with this? I am guessing by somehow mounting sdd1 somehow and sda1 the 1Tb drive I want to use for backup? Is there a command I could try? Pasting the commands from the errors recommended I use -ro but this also did not work.

- Is there a command to display partition labels, it may make this easier?

- Is there something now wrong with the BACKUP 1TB drive, or can I start copying files to it?

After running scandisk on the partitions that were visible in Windows 10, on Ubuntu I can now access at least the partitions just by clicking them from the launcher, Temp Backup (this is where I will be copying files to), WINXP, UBUNTU, HOME, OLD DUMP, and DUMP :)

```
abcd@roadrunner:~$ sudo lsblk -o name,mountpoint,label,size,uuid
NAME   MOUNTPOINT LABEL         SIZE UUID
sda                           931.5G 
&#9492;&#9472;sda1            Temp Backup 931.5G E6565F12565EE2BB
sdb                           298.1G 
&#9500;&#9472;sdb1            WINXP        55.7G 71FF83E7669614CE
&#9500;&#9472;sdb3                            1K 
&#9500;&#9472;sdb5            UBUNTU         15G 57b7cc02-c00b-49ea-8873-b3918feb9eea
&#9500;&#9472;sdb6            HOME         13.8G 47adf8d9-0d98-4d8f-8358-db60391ff3c9
&#9500;&#9472;sdb7            OLD DUMP    209.6G 4442D7A83361F05F
&#9492;&#9472;sdb8                            4G 
[I]sdc                           232.9G 
&#9500;&#9472;sdc1 /boot/efi  boot            1G 6DB9-DE8E
&#9500;&#9472;sdc2                          100G C680D55D80D55511
&#9500;&#9472;sdc3 /home                  117.2G ec25f59b-765a-489b-8b90-3a9756b0a495
&#9492;&#9472;sdc4 /                       14.7G 5ee8bbe0-319c-4a0e-8ae1-359b718ccc53[/I]
sdd                             1.8T 
&#9492;&#9472;sdd1            DUMP          1.8T 551E7B85560EBEA9

```

I could have sworn something was encrypted and I could not access it when I tried before...

---

