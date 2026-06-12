---
title: "Ubuntu 18.04.1 - Installation partitions scheme assistance"
date: 2018-10-21
forum: Installation &amp; Upgrades
---

### Post by pardeep.saini on 2018-10-21
Hello,
I'm going to install Ubuntu as my only OS, but I need help with the partitions scheme.
I have an SSD + HDD configuration, the SSD is 250GB and the HDD is 1TB.

After some searching I think this might be a "good" (not sure if actually good [IMG]https://ubuntuforums.org/images/icons/icon11.png[/IMG]) partition scheme, but I'll like to have a confirm:
SSD
/boot > 512MB
/ > rest of the SSD
HDD
/swap > 16GB (PC has 16GB of RAM)
/var > 16GB
/home > rest of the HDD

Thanks.

---

### Post by sp40140 on 2018-10-21
I suggest you let installer take care of everything. You don't really have to put /boot and /var and /home on different partitions. And as to swap, forget it, no need to swap partition at all. let installer create a 2gig swapfile, it is more than enough.
If you really want to have different partitions, you can give about 35gigs to / and rest of the ssd to /home. And mount the HDD to some other location.
It's simpler and easy to maintain.
I tell you this as you ask about the partition scheme. If you have to ask, keep it simple. If you know what/why, in that case make it complex and this forum will help with "how" of it.

---

### Post by pardeep.saini on 2018-10-21
The whole target of the partition scheme I'm trying to achieve is to avoid unneccesary SSD wear, so reading online they suggested to put /var and /swap on the HDD to decrease SSD wear.

If I decide to go without /swap partition where will the swapfile will be created? on the SSD or the HDD?
Is the swapfile a new thing? I haven't read about it before, I thought there was always a /swap partition.

So if I'm right the scheme you are suggesting is:
SSD
/ > 35GB
/home > rest of the SSD
HDD
some other location > what does that mean?

---

### Post by sp40140 on 2018-10-21
> **pardeep.saini said:**
> The whole target of the partition scheme I'm trying to achieve is to avoid unneccesary SSD wear, so reading online they suggested to put /var and /swap on the HDD to decrease SSD wear.

If I decide to go without /swap partition where will the swapfile will be created? on the SSD or the HDD?
Is the swapfile a new thing? I haven't read about it before, I thought there was always a /swap partition.

So if I'm right the scheme you are suggesting is:
SSD
/ > 35GB
/home > rest of the SSD
HDD
some other location > what does that mean?

if you don't create /swap, installer will automatically create a swap file.
The location, check out this link:  [https://askubuntu.com/questions/904628/default-17-04-swap-file-location](https://askubuntu.com/questions/904628/default-17-04-swap-file-location)

/ you can make it as big as you want, I prefer to keep it around 35 - 40 gigs.
HDD on other location : just that you can mount it on other location.

The /swap partition is from the time past when systems didn't have much RAM. These days if you have anything more than 6 gig of ram, swap is not required at all. However, in some rare cases few application do require swap (either file or partition) even if there is enough ram. This is the reason, Ubuntu installer by default doesn't create swap partition (and doesn't ask for it) but just silently creates 2GB swap file automatically.

---

### Post by oldfred on 2018-10-21
I have same SSD & HDD sizes. But do not have large data requirements, so have several / (root) partitions and a shared /mnt/data partition. The backup partition is not really a true backup as it is just a copy at a point in time.  My backups are then to DVDs & flash drives and other PCs. I boot ISO directly from grub so have separate partition on each drive for install to other drive. And drives are not yet fully allocated. 
```

fred@Bionic-Z170N:~$ sudo parted -l
[sudo] password for fred: 
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name    Flags
 1      1049kB  53.5GB  53.5GB  fat32        ESP     boot, esp
 2      53.5GB  86.0GB  32.5GB  ext4         xenial
 4      86.0GB  113GB   27.3GB  ext4         bionic
 3      228GB   250GB   22.0GB  ext4         ISO


Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  536MB   535MB   fat32           EFI System Partition  boot, esp
 2      52.5GB  85.0GB  32.5GB  ext4            bionic_b
 5      85.0GB  118GB   32.5GB  ext4            server
 6      118GB   443GB   325GB   ext4            data
 4      786GB   945GB   158GB   ext4            backup_b
 3      945GB   998GB   53.5GB  ext4            ISO_b
 7      998GB   1000GB  2202MB  linux-swap(v1)
```

---

### Post by pardeep.saini on 2018-10-22
> **oldfred said:**
> I have same SSD & HDD sizes. But do not have large data requirements, so have several / (root) partitions and a shared /mnt/data partition. The backup partition is not really a true backup as it is just a copy at a point in time.  My backups are then to DVDs & flash drives and other PCs. I boot ISO directly from grub so have separate partition on each drive for install to other drive. And drives are not yet fully allocated. 
```

fred@Bionic-Z170N:~$ sudo parted -l
[sudo] password for fred: 
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name    Flags
 1      1049kB  53.5GB  53.5GB  fat32        ESP     boot, esp
 2      53.5GB  86.0GB  32.5GB  ext4         xenial
 4      86.0GB  113GB   27.3GB  ext4         bionic
 3      228GB   250GB   22.0GB  ext4         ISO


Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  536MB   535MB   fat32           EFI System Partition  boot, esp
 2      52.5GB  85.0GB  32.5GB  ext4            bionic_b
 5      85.0GB  118GB   32.5GB  ext4            server
 6      118GB   443GB   325GB   ext4            data
 4      786GB   945GB   158GB   ext4            backup_b
 3      945GB   998GB   53.5GB  ext4            ISO_b
 7      998GB   1000GB  2202MB  linux-swap(v1)
```

It is a bit complicated for me to understand all of the configurations that you have done.
Basically, if I'm not wrong, you have SSD for / (root) and HDD for data?

> **sp40140 said:**
> if you don't create /swap, installer will automatically create a swap file.
The location, check out this link:  [https://askubuntu.com/questions/904628/default-17-04-swap-file-location](https://askubuntu.com/questions/904628/default-17-04-swap-file-location)

/ you can make it as big as you want, I prefer to keep it around 35 - 40 gigs.
HDD on other location : just that you can mount it on other location.

The /swap partition is from the time past when systems didn't have much RAM. These days if you have anything more than 6 gig of ram, swap is not required at all. However, in some rare cases few application do require swap (either file or partition) even if there is enough ram. This is the reason, Ubuntu installer by default doesn't create swap partition (and doesn't ask for it) but just silently creates 2GB swap file automatically.

Thanks for your time and explanations.
I have another question, what is the reason to divide / from /home even if they are both on the SSD, couldn't it be / on entire SSD?
I have also read about symlinks to link SSD /home folders to folders on the HDD, is it somehow similar to mount the HDD on other location?

---

### Post by oldfred on 2018-10-22
The / (root) partition does not need to be large. I keep /home inside / only for the mostly hidden user settings. I move some large hidden data folders like the Thunderbird & Firefox profiles to my data partition.

If a newer user, easier to have a separate /home and then you can have it on the HDD. One advantage of separating system from data is for backup and then reinstall if issues or new install of newer version. If you want the somewhat more advanced separate data partition and linking you also have to understand mounting, ownership & permissions. The separate /home automatically takes care of that.

But if not using SSD for anything else, your / will only use 10 to 20GB of whatever size partition you make. I currently have used 7.3GB of my 25GB / partition. My older 16.04 install used 13GB. I try to houseclean regularly so logs do not get large and lots of cruft gets removed, but some always seems to stay hidden, so I like new installs. And since I have space, I just install to another 25 or 30GB partition.

---

### Post by sp40140 on 2018-10-22
Like OldFred said:
The reason for splitting up / and /home is to keep data and system different. and in the even of crash or other issues, your data is on different partition which is more safe.
You don't have to. I did it for a while some years ago but don't split it anymore.
Different partitions help in enterprise / business environment where data and system needs to have tighter access control and reliability requirements.
For home use, I prefer to keep it as simple as possible. (Unless of course, you want to learn and experiment).

---

### Post by pardeep.saini on 2018-10-23
I think I'll go with this:
**SSD**
/
/home
**HDD**
/home folders with symlinks

I'll see in the future if I need to change something.
Thanks to both of you guys.

---

