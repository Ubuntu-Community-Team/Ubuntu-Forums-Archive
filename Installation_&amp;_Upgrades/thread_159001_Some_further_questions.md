---
title: "Some further questions"
date: 2006-04-12
forum: Installation &amp; Upgrades
---

### Post by Rhapsody on 2006-04-12
I posted here yesterday with some questions about installing Kubuntu and most of them were answered fully. I'm almost ready to start installation now, but I have a few queries left before I reboot and begin.

First, I was pointed to [this](http://users.bigpond.net.au/hermanzone/) site, which has cleared up pretty much all of the partitioning questions I had. But I've now found [this](http://users.bigpond.net.au/hermanzone/p14.htm) page on the same site, explaining how to make a seperate /home partition, and it seems quite interesting. I'll have 25GB of room to do all this in, which should be enough. My plans are for a 5GB root partition (primary) where Kubuntu will go at the start of the free space, and a 20GB /home (also primary) partition after that, with an extra 49.5GB of free space to arrive eventually when my Windows XP partition is deleted. With the swap partition on another drive, this will leave me with three primary partitions on one drive and two primary partitions on the other. Does this sound good to everyone?

Second, my plan to continues reading and writing to an NTFS partition I current have is to use [Captive NTFS](http://www.jankratochvil.net/project/captive/). I already have my current ntfs.sys file fully backed up, so I have no problems there. What I want to know is how reliable and usable Captive NTFS is. Is it suitable for regular writing of large (1GB+) files to an NTFS partition? Am I likely to get any corruption of data? Any user experiences would be welcome.

---

### Post by Sef on 2006-04-12
> Does this sound good to everyone?

How much ram do you have?  If you 1 GB or more, you don't need a swap.  If you have less, you should have a swap that is double your ram.

---

### Post by Rhapsody on 2006-04-12
[QUOTE=Sef]How much ram do you have?  If you 1 GB or more, you don't need a swap.  If you have less, you should have a swap that is double your ram.[/QUOTE]512MB. My current page file for Windows XP is 2GB (trust me, I've found way to use that kind of space) and I plan for my Kubuntu swap partition to be the same size and on the same drive. The drive is 232GB and not even half used, so it's not as if I'm desperate for space.

---

### Post by Rhapsody on 2006-04-12
My previous questions still stand unanswered, but I have further questions about which file system to use. The default is ext3, but I've been looking at ReiserFS and XFS as well. XFS in particular looks very powerful and versatile. Is there any particular reason I should use one of these file systems over the others?

---

### Post by Rhapsody on 2006-04-12
OK, summary of my questions.

1) My idea for partitioning goes as follows.

Smaller drive:
49.5GB FAT32 bootable primary partition with Windows XP on it.
5GB ext3/ReiserFS/XFS bootable primary partition with Kubuntu Linux on it.
20GB ext3/ReiserFS/XFS non-bootable primary partition as /home.

Larger drive:
231GB NTFS non-bootable primary partition with various data on it.
2GB swap partition for Kubuntu.

Am I likely to have any problems? Will this work? Is 5GB enough for Kubuntu to work with? Can Kubuntu be installed on a ReiserFS or XFS filesystem?

2) Captive NTFS. Is it reliable? Is it safe? Is it easy to use? Will I be able to live with it on a daily basis? Has anyone else used it?

3) Which filesystem should I be using? ext3, ReiserFS, or XFS. I like the look of XFS but there must be a reason why ext3 is the default. Are there things I should know about these filesystems? What are the pros and cons? Are any difficult to use? Will things not work if I use one of them?

I'm desperate to finally install Kubuntu, but I'm not confident enough to do anything until I have these questions answered.

---

### Post by dbd on 2006-04-12
Not sure about questions 2 and 3, but in reply to the first part of number 1, yes, 5 GB will be plenty.

---

