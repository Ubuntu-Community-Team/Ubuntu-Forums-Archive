---
title: "Unbuntu cant use my hardrive"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by fraz1993 on 2010-12-01
I recently upgraded from 9.04 to 10.04LTS , i wanted to start a fresh and i click the option for Ubuntu to use entire hard-drive. However on closer inspection Ubuntu has created two partitions , one sized at 289 GB and the other at 8.5GB the 8.5GB partition is the one with the os installed on it. It is sadly locked and i cant combine the two partitions :/.

[[IMG]http://img151.imageshack.us/img151/9789/screenshotvwu.th.png[/IMG]]("http://img151.imageshack.us/i/screenshotvwu.png/")

Thats a screenshot of the problem :( please help.

---

### Post by Zimmer on 2010-12-01
I cannot quite read the details from the gparted screenshot so need details of how Ubuntu has divided the disk.
but this does mean you can use the rest of the disk usefully.

What you need to do is look up stuff on partitioning and how to use gparted.

I will find you some good reading and post later.

For example, my disk is partitioned with a similar size Ubuntu partition, a couple of similar partitions containing Linux Mint and PCLinuxOS and a giant chunk of space which I store all my important documents and data on (not in the Ubuntu partition!)
This means if anything goes odd in an install or upgrade I can be fairly confident the data partition is safe and accessible. (and backed up elsewhere, too).

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

should get you started... take your time...

---

### Post by Zimmer on 2010-12-01
Not sure I am seeing the complete gparted screen on your screenshot. But the OS partition will be 'locked' as it is mounted .
From what I  can see a single EXTENDED partition has been created with LOGICAL partitions for the install. If this is not the full picture, let me know...

sda2 is the name of the EXTENDED partition which contains
sda5 sda6 sda7 as the LOGICALS.
sda5 and sda7 are  swap (extra paging memory like pagefile.sys in Windows)
sda6 is where the Ubuntu install is.

It would be better to have Operating systems on PRIMARY partitions. 
Suggest you repartition that drive and re install Ubuntu ( / root )to a specific partition, I suggest sda1 :)

For example: (Use the Live CD and use Gparted to do this.)
Delete the existing partitions to create Free space.

Create 3 PRIMARY partitions ( about 10Gig each ) and 1 EXTENDED from the remainder.

create a 2 gig swap partition in the Extended partition. You are then free to divide up the rest of the EXTENDED into partitions of whatever filesystem you require to act as storeage.

Then install Ubuntu to sda1.

Read more, and ask more questions :)

[http://members.iinet.net.au/~herman546/p17.html#Preparation_For_The_Install_](http://members.iinet.net.au/~herman546/p17.html#Preparation_For_The_Install_)

scroll down to partitioning rules on this page

---

