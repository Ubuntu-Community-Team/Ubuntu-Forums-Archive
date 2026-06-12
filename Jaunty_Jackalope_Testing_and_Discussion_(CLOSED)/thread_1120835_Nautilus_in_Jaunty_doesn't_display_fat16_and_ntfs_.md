---
title: "Nautilus in Jaunty doesn't display fat16 and ntfs partitions"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Shiba on 2009-04-09
Hi all, this is my first thread here, so I hope I didn't post it in the wrong place. I noticed that in Ubuntu Jaunty beta (and in the daily build too) Nautilus does not display my hd's fat16 and ntfs partitions. They are useless to me but I don't want to remove them, yet. Moreover, Jaunty got a problem in showing the correct names of my card reader.

Here it is how it is supposed to be (Fedora 11 beta): [http://dl.getdropbox.com/u/737114/bug/fedora.png](http://dl.getdropbox.com/u/737114/bug/fedora.png)
And here... how it actually is (Ubuntu 9.04 daily build 20090409): [http://dl.getdropbox.com/u/737114/bug/ubuntu.png](http://dl.getdropbox.com/u/737114/bug/ubuntu.png)

I know, no technical information, but I really don't know what kind of information to provide ^^'. I'd really like to resolve this problem, so just ask me for anything you need.

---

### Post by askreet on 2009-04-09
The "Computer" section in Nautilus displays all the mounted partitions.  Ubuntu GVFS apparently does not mount hidden FAT partitions by default.

Open a terminal and paste the output of:
$ gvfs-mount -l

I'm curious if it displays the hidden FAT partitions.

---

### Post by coffeecat on 2009-04-09
Yes, I agree with askreet. Dell utility and recovery partitions are almost certainly marked as hidden. Perhaps Fedora displays hidden partitions in computer:///.

If you want to check this out visually, install gparted. Then go to System > Administration > Partition Editor. That will show you all the partitions and will list whether any have the hidden flag set.

---

### Post by Shiba on 2009-04-09
Thank you for your replies. Here it is the output of gvfs-mount:

shiba89@shibapc:~$ gvfs-mount -l
Drive(0): Unità USB
  Type: GProxyDrive (GProxyVolumeMonitorHal)
Drive(1): Unità USB
  Type: GProxyDrive (GProxyVolumeMonitorHal)
Drive(2): Unità di memorizzazione
  Type: GProxyDrive (GProxyVolumeMonitorHal)
  Volume(0): Supporto da 10,7 GB
    Type: GProxyVolume (GProxyVolumeMonitorHal)
  Volume(1): Supporto da 285,6 GB
    Type: GProxyVolume (GProxyVolumeMonitorHal)
Drive(3): Unità CD-RW/DVD±RW
  Type: GProxyDrive (GProxyVolumeMonitorHal)
Drive(4): Unità USB
  Type: GProxyDrive (GProxyVolumeMonitorHal)
Drive(5): Unità USB
  Type: GProxyDrive (GProxyVolumeMonitorHal)

I tried looking with gparted, right click &#8594; Manage flags, but the flag "hidden" isn't checked in the both of them :(

---

### Post by dcstar on 2009-04-09
> **Shiba said:**
> Hi all, this is my first thread here, so I hope I didn't post it in the wrong place. I noticed that in Ubuntu Jaunty beta (and in the daily build too)
.........
I know, no technical information, but I really don't know what kind of information to provide ^^'. I'd really like to resolve this problem, so just ask me for anything you need.

There is a reason that **all** pre-release software problems **must** be posted in the development forum.

---

### Post by overdrank on 2009-04-10
Moved to  Jaunty Jackalope Testing and Discussion

---

### Post by Shiba on 2009-04-10
@overdrank, dcstar: thx, I didn't notice this category, I'll keep in mind for the next time :oops:

---

