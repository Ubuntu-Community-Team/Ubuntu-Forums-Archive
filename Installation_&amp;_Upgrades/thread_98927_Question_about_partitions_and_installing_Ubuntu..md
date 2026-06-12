---
title: "Question about partitions and installing Ubuntu."
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by Royle on 2005-12-04
I already have a drive partitioned how I like it.  It has one / partition, a swap partition and a /share partition that is formatted in FAT32.  I don't want to lose the data on my /share partition, will this be a problem?  Thanks in advance for your help.

---

### Post by bwog on 2005-12-04
There is a login problem that is related to fat32 partitions. I dont know if it applies here. But you are prepared now: [http://ubuntuforums.org/showthread.php?t=89992&highlight=login](http://ubuntuforums.org/showthread.php?t=89992&highlight=login)

When you make partitions before install you have to mount them during install.

I am not familiar with a /share partition. I have /home and extra partition in ext3 called /media/sdb7.

You probably dont need a share partition. You can read ext3 from windows with explore2fs. Normally you would make a /home partition.

---

### Post by az on 2005-12-04
[QUOTE=Royle]I already have a drive partitioned how I like it.  It has one / partition, a swap partition and a /share partition that is formatted in FAT32.  I don't want to lose the data on my /share partition, will this be a problem?  Thanks in advance for your help.[/QUOTE]
During the install, you can tell the partitioner to do manual partitioning.  You will then be show the list of partitions.  On your partition you are using as root, tell it to format that partition and mount it as root (/).  On you current share partition, tell it to keep existing data and give it a label (share)  You will have a mountpoint in ftsab after you do that.

It will not touch your data there, if you do that.

---

