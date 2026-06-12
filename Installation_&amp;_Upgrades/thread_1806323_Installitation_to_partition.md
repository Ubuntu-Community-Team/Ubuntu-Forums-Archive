---
title: "Installitation to partition"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by duryard on 2011-07-17
This may seem a bit ambitious or even wired or just wrong but I have come up with a plan. I want to install ubuntu to a separate partition.

I have vista on one partition
XP Pro on another partition and thought I might put ubuntu on another.

The HD is already partitioned into 4
1 XP
1 Vista
1 backup
1 for ubuntu

I have worn google to a frazzle trying to find out how to make 11.04 install to a partition and still cant get it sorted.

Any help would be appreciate. Even stuff like "Dont be silly, you cant do that"

---

### Post by oldfred on 2011-07-17
You need to convert the Ubuntu partition to an extended partition so you can create at least two partitions and maybe an additional for /home and perhap a shared. (Note I like lots of partitions with 16 on my sdc 640GB drive.)

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

With two copies of windows grub will only find one as windows has moved all the boot files to the first install. You then have to boot windows and choose which windows to boot.
To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Split dual boot win7 & XP - Instructions meierfra. post #3
[http://ubuntuforums.org/showthread.php?t=1421737](http://ubuntuforums.org/showthread.php?t=1421737)

---

### Post by duryard on 2011-07-17
The partitions are about 100 GB each.

So basically I nee to setup all the little partitions

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

for ubuntu on the one Partition I have already reserved for ubuntu?

---

### Post by oldfred on 2011-07-17
Do not use windows to create partitions. It converts to dynamic which is not compatible with anything including some windows things.

Ubuntu does not need a large system partition and I suggest keeping data separate from systems. The shared NTFS partition makes sense with three installs and two being windows. I put my Firefox & Thunderbird profiles in a shared now NTFS partition so I have the same bookmarks & email in all systems.

---

### Post by Bucky Ball on 2011-07-17
> **duryard said:**
> 
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical



Looks good. As mentioned, you will need to put those inside an extended partition as you can only have four primary partitions on one physical hard drive. 15Gb is probably plenty for / as your data will be stored in /home and I'd probably go EXT4. ;)

---

### Post by ManualSparrow on 2011-07-17
Also, when you boot your LiveCD/USB and select "Install" you can  select the "Specify partitions manually" option, which will open up GParted and let you change your last partition to "extended" and then create your 3 new partitions inside it.

---

### Post by Blasphemist on 2011-07-17
On the current version live cd's, natty 11.04, the partition manually option is accessed by choosing "something else" on the allocate drive space screen.

---

