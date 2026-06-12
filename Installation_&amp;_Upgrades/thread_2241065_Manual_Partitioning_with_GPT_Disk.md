---
title: "Manual Partitioning with GPT Disk"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by LibreCoupon on 2014-08-23
I'm not new to Ubuntu. I'm not new to partitioning. But I'm new to GPT Disks.
As with my previous experience installing and partitioning Ubuntu/other distro on an older hard disks, I partition my hard drive as follows:

/boot - 512mb
/ - 100Gb
/home - 500Gb +
/swap - approximately 16Gb


With GPT Disks, I don't know how to partition these newer disks.

I've bought a new laptop with Windows 8.1 installed. It has a GPT Disk. Can I still partition this disk using the same partitions above?
Or will there be an additional partition that should be created for a GPT Disk?

I still want to assign at least 100Gb for / and at least 500Gb for /home. I have a lot of videos and music. I download a lot of movies so my /home partition should be on a separate partition. I'm not sure if 100Gb is just too big for / but I usually install Skype, Filezilla FTP Client, GIMP, Inkscape, WINE, and VirtualBox. Sometimes I need to run a file that is specific to windows and VirtualBox is my only option. I'm not sure though if VirtualBox files are stored on /home or on another directory/folder.

---

### Post by LibreCoupon on 2014-08-24
It's a lot harder than I thought. I always ended up with a GTP Tables error.
I just selected to replace windows and automatically creates 3 partitions. 
- FAT
- / 
- SWAP

I just stick with this setup for now. I want to use the OS as soon as possible.

---

### Post by grahammechanical on 2014-08-24
From what I have read on this forum I would not expect to have problems with partitioning with GPT. The problems come with Windows 8 pre-installed and whether we are installing in the same mode (EFI or legacy) that Windows 8 was installed in.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

Here are some information but not part of the Ubuntu wiki.

[http://www.linuxbsdos.com/2014/02/05/gpt-disk-partitioning-guide-for-ubuntu-13-10-on-a-pc-with-uefi-firmware/](http://www.linuxbsdos.com/2014/02/05/gpt-disk-partitioning-guide-for-ubuntu-13-10-on-a-pc-with-uefi-firmware/)

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

[http://www.linux.com/learn/tutorials/730440-using-the-new-guid-partition-table-in-linux-good-bye-ancient-mbr-](http://www.linux.com/learn/tutorials/730440-using-the-new-guid-partition-table-in-linux-good-bye-ancient-mbr-)

Regards.

---

### Post by fantab on 2014-08-24
Boot with Ubuntu DVD/USB and 'Try Ubuntu'.
Post the output of the following:
```
sudo parted -l
```

Edit: I didn't see this:
> I just selected to replace windows and automatically creates 3 partitions. 


So you installed Ubuntu already replacing windows?

---

### Post by oldfred on 2014-08-24
If starting from scratch, you have to tell gparted you want gpt over the default MBR(msdos). But if it sees that drive is already gpt you can just use gparted like you do with MBR, but do not have to worry about extended and logical partitions.

On a larger drive, I do not like default install as it makes a huge / (root). Better to have /home and/or separate data partitions.

 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)


I make / either 20 or 25GB including /home end up using 7.4GB on new not quite fully configured 14.04 and 12GB on my 12.04 that maybe needs more housecleaning.

```
fred@trusty-DT:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd4        28G  7.4G   19G  29% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           396M  1.4M  394M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  140K  2.0G   1% /run/shm
none            100M   52K  100M   1% /run/user
/dev/sdc2       100G   43G   58G  43% /mnt/shared
/dev/sdc6        96G   47G   45G  52% /mnt/data
/dev/sdd3        28G   12G   15G  44% /media/fred/Precise

```

All my data including some of the normally hidden folders in /home that have more data like Firefox & Thunderbird profiles as in my two data partitions. One is still NTFS from when I still booted XP, but all new data goes into Linux data partition.

---

