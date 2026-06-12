---
title: "Move entire install to another disk"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by ThaddeusW on 2008-04-09
Ok I have seen some other posts related to this topic but I want a simple step by step method of moving my install from one disk to another using the command line. I am upgrading to 7.10 from 6.10 but this machine is a bit old and I want to make sure the install goes smoothly. I need to make sure it runs perfectly before I wipe out my current install. 

My plan goes like this:

backup home directory on current 80gb dapper disk and disconnect it. 
use an old but working 10gb hard disk for gutsy 7.10, install and test
either rm -rf / or just format the primary partition of the dapper disk after reconnecting
copy everything from 10gb gutsy disk to 80gb disk. 
Reinstall grub
enjoy new 7.10 on 80gb disk.   

My only question is how do I copy the contents and preserve the permissions? I know if I use cp as root everything will be owned by root. Another user posted this code:
```

mount /dev/hdd2 /media/backup
cd /
tar --exclude=/tmp vcf - . | ( cd /media/backup/backup ; tar xvpf - )
umount /media/backup
```

I am guessing piping the output of tar to the target 80gb disk will preserve the permissions etc. 

Is this a good idea or is there a better way? Oh and I want to do this via command line by my self. no scripts or utils. I want to learn the "hard" way :).

---

### Post by fela on 2008-04-09
what i would do is reinstall Gutsy on the 80gb, then transfer all your data onto that installation. Rather than install on the wrong disk then somehow transfer the installation onto the 80gb one.

---

### Post by Pumalite on 2008-04-09
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

### Post by warp99 on 2008-04-09
No need to copy everything to a separate drive. Just boot to a Ubuntu Install disk, then using gparted shrink you current partition to make space for a 10 GB parition, then make the 10GB partition. Mount both partitions manually, then copy the files from partition one to partition two. You can use a separate hard drive if you don't want to partition your current drive. 

Example:

Boot to you 7.10 Ubuntu install CD, use gparted to shrink then make the second partition. Partitions are now /dev/sda1 and /dev/sda2, so we mount them:

```
mkdir /media/sda1
mkdir /media /sda2
mount /dev/sda1 /media/sda1
mount /dev/sda2 /media/sda2 
```
then copy the file from one to another:
```
cp -prv /media/sda1/* /media/sda2/
```
the -p parameter does this, from the 'man cp' pages:
```
-p     same as --preserve=mode,ownership,timestamps

       --preserve[=ATTR_LIST]
              preserve   the   specified   attributes   (default:  mode,owner&#8208;
              ship,timestamps), if possible additional attributes: links, all
```
after that unmount the drives:
```
umount /dev/sda1
umount /dev/sda2
```
then install 7.10 to partition /dev/sda1.

Edit:

Remember to use the same user number (UID) and group number (GID) as your previous install, which should be 1000 for both.

---

### Post by Pumalite on 2008-04-09
From Herman's Site:

Copy and Paste the whole partition with GParted
This was the original method I had here, I'll still keep it here for a while in case it's useful to anyone. This was my favorite method for a long time. Filesystem UUID numbers have now made this method a little bit more complicated than it used to be. With GParted, the new partition will be given the original partition's UUID number, however it will have a new partition number.
The original partition, on the other hand, retained its partition number, and but was given an new filesystem UUID. This means it will be necessary to check both /etc/fstab and also grub's menu.lst to make sure they have the current UUID numbers.

---

