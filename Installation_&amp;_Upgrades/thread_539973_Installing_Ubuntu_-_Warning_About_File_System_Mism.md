---
title: "Installing Ubuntu - Warning About File System Mismatch"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by mcguirkp on 2007-08-31
Hello,

   I am trying to install Ubuntu 7.04 on an existing Windows box.  I ran gparted and partitioned my drives as follows:

/dev/sda1  fat16   - very small
/dev/sda2  ntfs
/dev/sda3  ext3    - bootable
/dev/sda4  extended
/dev/sda5  linux-swap
/dev/sda6  fat32

   This is an older Dell box.  The first two partitions were already present.  I removed one partition which contains the system restore and added sda3 through sda6.
   Then, when I reboot with the installation CD, it runs fine until the Prepare Partitions screen.  I get the following Warning message:

  "File system doesn't have expected sizes for Windows to like it.  Cluster size is 2k (1k expected); number of clusters is 24026 (47959 expected); size of FATs is 94 sectors (188 expected)."     Ignore | Cancel

  I don't want to screw up the Windows installation.  Can I safely Ignore this message?  Or, should I change some setting. 
  Any help appreciated.

Regards,
Pat

---

### Post by louieb on 2007-09-01
I've done a lot of installs on old and new systems. Never seen that message. Don't think I'd do anything else until I had a full backup. If all you did was split the restore partition up  into 3 other partitions it seems they would be to small. How big are they? It would also help if you could post a screen shot of the GParted window. Also where did you get the message? In the first partitioning screen or in the manual partitioning screen? Since you set up your partitions in advance you will have to use the manual partitioning option.

---

### Post by diatribe on 2007-09-01
why would you make another fat32 partiton?  and what partion was the error referring to

---

### Post by mcguirkp on 2007-09-01
Hello,

  Thank you for your responses.
  Below is a screenshot of the error, along with the configuration of the hard drive in the background.  I should have mentioned that I resized the NTFS partition, so I should have plenty of room in other partitions.
  Also, the machine was from Dell and had contained 3 partitions (from factory).  The first partition is FAT16 & I can only guess they use it in conjuntion with their system restore.  I decided to leave that partition alone  & add a much larger FAT32 to share data between Windows & Linux.  I would then install GRUB (or whatever its called) into the ext3 partition.
  The error seems to relate to sda1.
  I am tempted to ignore the error & try to press on....I just don't want sda1 & sda2 to somehow get corrupted, so I wanted to ask the experts out there for your opinion.
Regards,
Pat

[IMG]http://www.patrickmcguirk.com/WarningMsg.jpg[/IMG]

---

### Post by louieb on 2007-09-01
If it is booting windows now there is a good chance that it will continue to boot after the install. But I stand by my backup your data statement. Your have gone past the part most dangerous to your data. That is the shrinking of the NTFS partition and the creation of the new partitions. The install should not touch sda2.  Looks like a well thought out partition plan. Except for the warning message it all look good.  The  only thing that I wonder about is that GRUB expects the Window boot code to start in the  standard place that is sector 63 if I remember right.   Might want to have a Windows boot disk handy. :guitar:

---

### Post by mcguirkp on 2007-09-01
OK - thanks for your help.  I went ahead with the installation & everything turned out fine.

Thanks again,
Pat

---

