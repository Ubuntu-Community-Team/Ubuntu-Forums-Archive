---
title: "How to deal with the file system changes?"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by Benta on 2008-08-23
Friends,

I have two extra controllers for hard disks on my machine, besides the one that the booting drive is on.

On those I have a couple of drives used for storage of a lot of data that I use across the network with samba. 

Those drives have previously been shared drives in samba. I mount them through fstab. This is very convenient and has worked well. 

After the upgrade, something has changed in the way ubuntu deals with the drives.

When I boot, the boot process stops at one point late in the process and gives some errors and leaves the stuff below in the log. I have to restart the booting process with ctrl-D, but then it boots OK.

First, I thought that the was a problem with reading the fstab. But I don't think so. Because the drives are listed under the "removable devices" with the correct name (label), and if I click on them, they mount to the place in the files system that is given in fstab.

Interesting is also that the devices no longer show up under dev (as /dev/hdd1 and so on). They are never there.

Does anyone know how I can get rid if these issues?


-------
Log of fsck -C3 -R -A -a 
Sun Aug 24 02:34:33 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/hdd1
/dev/hdd1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

---

### Post by Benta on 2008-08-23
> **Benta said:**
> Friends,

I have two extra controllers for hard disks on my machine, besides the one that the booting drive is on.

On those I have a couple of drives used for storage of a lot of data that I use across the network with samba. 

Those drives have previously been shared drives in samba. I mount them through fstab. This is very convenient and has worked well. 

After the upgrade, something has changed in the way ubuntu deals with the drives.

When I boot, the boot process stops at one point late in the process and gives some errors and leaves the stuff below in the log. I have to restart the booting process with ctrl-D, but then it boots OK.

First, I thought that the was a problem with reading the fstab. But I don't think so. Because the drives are listed under the "removable devices" with the correct name (label), and if I click on them, they mount to the place in the files system that is given in fstab.

Interesting is also that the devices no longer show up under dev (as /dev/hdd1 and so on). They are never there.

Does anyone know how I can get rid if these issues?


-------
Log of fsck -C3 -R -A -a 
Sun Aug 24 02:34:33 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/hdd1
/dev/hdd1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

And oh, tht drive has an ext3 file system (and works fine after manual mounting). Not sure why it says ext2.

---

### Post by Pumalite on 2008-08-23
Check your UUID's:
blkid
Against /etc/fstab and /boot/grub/menu.lst

---

### Post by paped on 2008-10-19
I have just upgrade from 7.10 to 8.04 and have the same problem and error message above about just one of my drives hdd1. Did you ever manage to resolve this issue if so how....?

My system specs are 1Ghz Via ITX PC, 1GB of ram, I use a single motherboard based HD controller with 4 HD's

hda - 500Gb Vfat
hdb - 80Gb EXT3 (system/swap partitions)
hdc - 200Gb EXT3
hdd - 300Gb (split in to 3 partitions all EXT3)

Running "server" distro, with Gnome added, but due to the ITX having a few issues with the Server kernel I am using the "generic" one everything was working OK under 7.10

Now I have done a bit of testing with this and I think that it may be something to do with the kernel in 8.04. Basically when I boot using the kernel that comes with 8.04 (generic 2.6.24-21) I get the same error that is posted above against hdd1 including reporting the drive as EXT2 when it is EXT3 and the system drops to command prompt and refuses the go any further. When I use GRUB to select the older kernel (generic 2.6.22-15) the system boots up fine with all HD's including HDD1 working correctly...

I have used Linux for a few years now but I need help trying to fault find something like this as I must admit I don't know where to start. As such if anybody knows how to fix this or can give me some pointers regarding testing it further it would be greatly appreciated.

---

### Post by paped on 2008-10-19
I have noticed one other issue when I try to write to the samba shares I have configured on this system the whole system locks up and need to reboot before being accessible again....

---

