---
title: "How to partition Harddrive into 3 partitions?"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by hhtmp88 on 2010-01-31
Dear all,

I am using WinXP and partitioned my 160GB harddisk into 3 partitions:
1. program drive c: (20GB) --  for winXP OS and other applications
2. data drive d: (100GB) -- for storing data, photos, audio and video files
3. backup drive e: (40GB) -- for storing the backup of program drive (using Acronis True Image)

so my question is:  how to do the same if I am using Ubuntu 9.10?

Thanks for any kind of help!
Rgds,

---

### Post by audiomick on 2010-01-31
Hallo.
The standard partitioning tool in Ubuntu is gparted. It is available to download (if not already installed) via the synaptic package manager, or using the command
```
sudo apt-get install gparted
```
It is also installed on the live CD, if you boot using the "try without changing" option, or as a gparted live CD
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If you are using a new drive, you just have to create the partitions. During the installation of Ubuntu, if you choose the "manual" option you can designate partition structure however you want.

If you are using the drive you described in your post, you will need to shrink the partitions you have to make room (backup first), create an Extended partition and create your Linux partitions as logicals inside that ( you can only have 4 primary partitions on a drive, or 3 primary and 1 extended with up to 64 logicals inside.)

Ubuntu can read a NTFS partition, but windows cannot read any Linux file system types.

Here is some info on partitioning.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by hhtmp88 on 2010-01-31
Thanks Michael for your quick response!

I am going to buy a new full HD media pc, Giada N10, and partitioning is to done in this new media pc,
-> so am I right that I can do the partitioning during Ubuntu installation?
-> or must I do that after Ubuntu installation?


and after partitioning, how can I configure Ubuntu to store all configurations and data directories in the second partition (i.e the data partition)?

Besides, any good suggestion for system backup, i.e. any Ubuntu counter application for Acronis True Image? 

Rgds,

---

### Post by audiomick on 2010-02-01
Hi.
Sorry for the delay, I went to bed.

Partitioning should be done during the install. You can change partitions later with gparted, but it is easier to set it up the way you want from the start.
If you don't want to use the default partitions setup, which seems to be the case, choose the "manual" option at partitioning time during the install.

You can cause Ubuntu to save things to places other than the default by changing the default storage paths of the relevant programs (usually possible in the "preferences" settings of the respective program), or by creating symlinks in your home folder. I haven't done that, so I can't talk you through it. There is some info here
[http://manpages.ubuntu.com/manpages/hardy/man2/symlink.2.html](http://manpages.ubuntu.com/manpages/hardy/man2/symlink.2.html)

As far as backups go, I have seen a lot of recommendations for rsync
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

On that page, the link to the Backup your system series
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
looks promising.

---

### Post by oldfred on 2010-02-01
You can do partitions during the install or in advance. I plan a variety of partitions so I usually do it in advance with a separate live gparted download CD.

I had the standard install of just root (/) and swap fro the last three years but on update to Karmic created an additional root so every update I alternate installs. I moved /home to a separate partition and moved all my data to another partition and link that into /home. While I made my home partition sizable thinking I would need it, but with all my data linked in, my /home is less than 1GB.

[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

---

### Post by hhtmp88 on 2010-02-02
Thanks all for your great comments!
Will try them out!

As Giada N10 comes with a 320GB harddisk, is it a good choice to partition it with the following sizes:
1. program partition (10GB) --  for UNR(Ubuntu Netbook Remix) and other applications
2. data partition  (280GB) -- for storing data, photos, audio and video files
3. backup partition (30GB) -- for storing the backup of program partition (using rsync or gsync)

Information of Giada N10 can be found here:
[http://giada.cc/chanpinzhongxin/minipc/slim%20series/2009-10-30/1.html#ecms](http://giada.cc/chanpinzhongxin/minipc/slim%20series/2009-10-30/1.html#ecms)
[http://www.tweaktown.com/reviews/3050/giada_slim_n10_nvidia_ion_nettop_extremely_small_and_stylish/index9.html](http://www.tweaktown.com/reviews/3050/giada_slim_n10_nvidia_ion_nettop_extremely_small_and_stylish/index9.html)
[http://healthkb.org/g2/main.php?g2_itemId=2494](http://healthkb.org/g2/main.php?g2_itemId=2494)


and am I right that UNR support Intel Atom processor and nVidia ION Chipset?

Rgds,

---

