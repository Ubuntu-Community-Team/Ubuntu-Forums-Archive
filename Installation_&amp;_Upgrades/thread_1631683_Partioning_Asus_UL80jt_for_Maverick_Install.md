---
title: "Partioning Asus UL80jt for Maverick Install"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by fmhoyt on 2010-11-26
I'm getting reading to install 10.10 on my Asus UL80jt (64bit, 500gb hard drive), but would like some guidance on partitioning. The computer comes with Windows 7 and Express Gate, each on its own partition. If possible I would like to preserve these. I also assume that there is a hidden restore partition on the drive. 

The partitioner in the Ubuntu installer shows the following partitions: 

/dev/sda1  FAT32 17823mb 8386mb
/dev/sda2  NTFS  482282mb 88588mb

As far as I understand, the NTFS partition is the Windows 7 partition, and the FAT32 the Express Gate. I need to shrink one or both of these in order to create several partitions for Ubuntu. Which can be changed safely without foobar-ing the factory OSs? 

For what it's worth, I'm doing this after using a Wubi-installed Ubuntu for several months. This hasn't worked out: The power management is awful, and updates to Ubuntu frequently break the grub settings. 

Thank you in advance.

---

### Post by carl4926 on 2010-11-27
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)
You then need to backup and then defrag windows

Now get yourself Parted Magic
[http://partedmagic.com/download.html](http://partedmagic.com/download.html)

And shrink your main windows partition. But I do wonder if that partition info you quoted is correct.

This video shows how to shrink a partition, amongst other things. Ignore the partition sizes:
[http://dl.dropbox.com/u/10573557/Win-Install/Partitioning%20example%20win7-linux.mpeg](http://dl.dropbox.com/u/10573557/Win-Install/Partitioning%20example%20win7-linux.mpeg)

---

### Post by tommcd on 2010-11-27
After you create space for installing Ubuntu, here is a good beginners guide to partitioning. It shows you how to create separate root and home partitions during the install:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
The root partition is for the Ubuntu operating system and the home partition will be used to store your data and personal settings.
Write back if you need more help.

---

