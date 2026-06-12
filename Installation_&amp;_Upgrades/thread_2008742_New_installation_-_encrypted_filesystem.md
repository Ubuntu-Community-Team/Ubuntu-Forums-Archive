---
title: "New installation - encrypted filesystem"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by Blackbelt2011 on 2012-06-23
Being new with Ubuntu, I want to install 11.10 on** two 1.0TB HDs.**
I want to use the alternate install DVD and make 3 partitions on sda:

sda1: 800 GB primary / ext4
sda2: 800 GB logical /ext4 / (Complete filesystem except /home and swap)
sda5: 150 GB logical / ext4
sda6: 150 GB ext 4 (/home)
sda7: 050 GB swap

All space will be completely encrypted, so Ubuntu will create another small boot partition?

The second HD should have only one big partition:
sdb5: 1000 GB / ext4
sdb6: 1000 GB / ext4 (for storage of data)

I want to encrypt sdb5 also.

I want to have all filesystems mounted on booting.
What **mountpoint name **would be good for sda6? And can the installer write all that in the fstab during installation?

Is it working as I planned it? I am not experienced in partitioning.

Thanks,
Blackbelt2011

---

### Post by fantab on 2012-06-23
First of all I recommend [**GParted LiveCD**]("http://gparted.sourceforge.net/livecd.php") to manage Disk Partitons. 

Ok. You don't need 50GB SWAP, 2-4GB is more than enough. As for /dev/sdb6 I would suggest that you leave it formatted EXT4 without using any mountPoint and it will be Linux DATA partition. You can either mount it manually or automatically at system start.

I have two separate Hard Disks and this is how the partitioning Looks:

sda1- 20GB-ext4 Primary / ubuntu
sda2- 20GB-ext4 Primary / another Distro
sda3- 20GB-ext4 Primary / ubuntu development release
sda4- ? Extended
sda5- ? ext4 Logical DATA
sda6 4GB SWAP

sdb1- 1TB EXT4 Primary DATA

I manually mount my DATA Partition as and when I need them. Also notice I personally don't use /home.

Partitions are a very personal so be wise. There is plenty of information about ENCRYPTION on this forum just search.

---

