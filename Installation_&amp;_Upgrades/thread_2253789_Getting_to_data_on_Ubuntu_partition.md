---
title: "Getting to data on Ubuntu partition"
date: 2014-11-22
forum: Installation &amp; Upgrades
---

### Post by eljc2 on 2014-11-22
I have been running xubunu, which I installed using the wubi tool, alongside Windows 7.

I tried to upgrade to the latest LTS release of ubuntu, but unfortunately now ubuntu will not load. I am getting a memory error, which I suspect is because the newest version is trying to load up and use more memory. My netbook has a mere 1 GB of RAM.

To solve this, I think I will have to uninstall ubuntu through windows and then I can load it on again using a USB startup disk. However, first, I would like to get access to my data on the ubuntu partition so that I can recover files that were lost. This cannot be accessed through windows. I have tried running xubuntu in trial mode (from the USB stick). However, I don't think every partition is available. Here is what happens when I list the partitions:

xubuntu@xubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0   100G  0 part /media/xubuntu/F430478C304754B0
&#9500;&#9472;sda2   8:2    0    15G  0 part 
&#9500;&#9472;sda3   8:3    0 133.1G  0 part /media/xubuntu/60D85852D8582914
&#9492;&#9472;sda4   8:4    0    16M  0 part 
sdb      8:16   1   7.6G  0 disk 
&#9492;&#9472;sdb1   8:17   1   7.6G  0 part /cdrom
loop0    7:0    0 866.8M  1 loop /rofs

How can I mount everything, so that I can go in and have a look at my documents?

---

### Post by Impavidus on 2014-11-22
Wubi is deprecated. Don't try using it again. 1GB ram is small for Ubuntu. It may work, but very sluggish. You can indeed better try Xubuntu.

Your wubi-installed Ubuntu system doesn't have a partition of its own. Instead, it has a virtual partition, which is just a file on the Windows system. It is called root.disk and it is very large. You should be able to mount that file in the live session. Have a look here: [http://askubuntu.com/questions/243621/how-to-mount-root-disk-from-wubi-when-booted-from-dual-boot-install-of-ubuntu](http://askubuntu.com/questions/243621/how-to-mount-root-disk-from-wubi-when-booted-from-dual-boot-install-of-ubuntu). You may have to change to paths to match your situation. You may have to use sudo.

---

### Post by hakuna_matata on 2014-11-22
> How can I mount everything, so that I can go in and have a look at my documents?
If your Windows partition with Ubuntu is already mounted
> ```
&#9500;&#9472;sda1   8:1    0   100G  0 part /media/xubuntu/F430478C304754B0
```
or
> ```
&#9500;&#9472;sda3   8:3    0 133.1G  0 part /media/xubuntu/60D85852D8582914
```
then assign your Ubuntu to /dev/loop1 (/dev/loop0 is your live system)
```
sudo losetup -f /media/xubuntu/*/ubuntu/disks/root.disk

```
make a folder and mount your Ubuntu there:
```
sudo mkdir /media/xubuntu/wubi
sudo mount /dev/loop1 /media/xubuntu/wubi

```

---

### Post by eljc2 on 2014-11-23
Thanks for your help. I managed to get the files and I have not (after a lot of faffing around with partitions), removed the wubi from windows and installed xubuntu fresh from the USB.

---

