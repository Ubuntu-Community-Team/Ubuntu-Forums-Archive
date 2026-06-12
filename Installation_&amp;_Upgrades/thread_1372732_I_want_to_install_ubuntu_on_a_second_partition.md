---
title: "I want to install ubuntu on a second partition"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by ozzyto on 2010-01-04
ok, this is this:

I have a lap with a 500gb hdd with three part., 1. win, 2. ubuntu, 3. data. I installed ubuntu with wubi, but I want to install from the boot livecd directly, the problem is that when i get to partition step and I select partition 2 with 19gb, the installer told me something like  there is no set file system root or something, although I do not understand the booth method (/dos, /win) and the other option that have ntfs, jda... and so many option that I don't remember. In the same way, what is that of sda1,2,3,4,5, win, ubuntu, extended, /home. I am really new with ubuntu.

Thanks

---

### Post by oldfred on 2010-01-05
With the laptop you may have a hidden partition or two for recovery. You can only have 4 primary partitions or 3 primary and 1 extended that can contain many logical partitions.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

---

### Post by SecretCode on 2010-01-06
If you are struggling to understand what is currently on your disk, give us the output of the following command. Boot the installation CD, but select 'try ubuntu without any change to your computer'. When booted, click Applications > Accessories > Terminal, and enter the following command:
```
sudo fdisk -l /dev/sda
```

Copy the output and paste it here in between code tags [code]like this[/**code]
This is easier if you can run firefox from the live CD and log in here

---

