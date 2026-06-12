---
title: "Partition with W7"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Timper on 2009-12-26
I, the ever noob with linux need to know how to partition.

I have a brand new computer with Windows 7 already installed.

I want to make about 1/4 of my hard drive partitioned for ubuntu.
How would I go about doing this?  I don't want to mess up my computer and have to take it in to get fixed.

Oh, and step by step would be great, I am quite an idiot when it comes to over-generalized instructions that expect you to know 90% of the programs and terms they use.

---

### Post by oldfred on 2009-12-26
I have a lots of links that go into partitioning with lots of detail and screenshots so you have some idea of what you are doing before hand.
You should use the win7 tools to shrink the windows partition. You then can use the installer or if you want additional partitions it may be best to use gparted to create the partitions in advance and use the manual install to choose the already created partitions. It requires some planning on space available and what you want. As you get more used to Ubuntu your needs  will change and your next install may be different. My original install was just root (/) and swap with a shared NTFS partition for data I wanted in both windows and ubuntu like photos and profiles for firefox and thunderbird. Now I am mostly Ubuntu and have ext3 data partitions just for linux.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Info on partitions using gparted.
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

