---
title: "How do I mount an existing Fedora LVM after Kubuntu install?"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Erik765 on 2008-04-23
Hi,
I have a 500gb hdd with xp, and fedora8 installed. There are 170+gb free space after those two. I installed Kubuntu here.

I assumed that Kubuntu would edit grub to include kubuntu, xp as well as fedora, but it only does kubuntu and xp.

Unfortunately, the Fedora8 was installed as LVM, but all my files are here and want to be able to transfer betweed the kubuntu and fedora partitions.

I tried to make sure Kubuntu wasn't touching the LVM partition during install, but when I go to kmenu> System Settings> Advanced> Disk & Filesystems It's showing what should be a Fedora LVM as a mount point of /proc. What does this mean? There's nowhere to change that and I'm not sure I want to risk it. 


fdisk -l shows this:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeca89011

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3187 25599546 7 HPFS/NTFS
/dev/sda2 3188 19122 127997887+ 7 HPFS/NTFS
/dev/sda3 19123 19135 104422+ 83 Linux
/dev/sda4 19136 60801 334682145 5 Extended
/dev/sda5 19136 38913 158866753+ 8e Linux LVM
/dev/sda6 38914 39423 4096543+ 82 Linux swap / Solaris
/dev/sda7 39424 60801 171718753+ 83 Linux


fstab has this (looks like my windows partitions and my optical drive.)

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda7
UUID=335ad472-2db4-4ba5-b28f-febac34f4713 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=9E4837134836EA23 /media/sda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda2
UUID=58C0F711C0F6F45A /media/sda2 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda3
UUID=a9b0ea94-7d62-4b2a-b87f-76f05598c94b /media/sda3 ext3 defaults 0 2
# /dev/sda6
UUID=0324973b-4f17-4adb-b8bd-7c10deb06028 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0


I've thought about just adding /dev/sda5 to fstab but how do I find out its UUID?

I've tried using pvscan, but it doesn't see anything.

Gparted sees the partition but it's black and it displays it as unkown. Does gparted not deal with LVMs at all?

This is getting frustrating.

Help me out guys. I need those files off my LVM.

I can post grub's menu.lst from pre and post Kubuntu if needed 'cause I can kept copies before I did the install.

So far I like Anaconda LOTS better.

Any thoughts?

---

### Post by kunixos on 2008-12-29
You need to make sure you installation of Kubuntu includes support for LVM (it does not automatically) by installing the lvm2 package
```
apt-get install lvm2
```
Once the support is installed check GParted again to make sure it can recognize the newly supported filesystem type. Now you should be able to add it to your menu.lst by using the tags from the Fedora grub/menu.lst (the UUIDs, etc).

Let me know how this works!

---

