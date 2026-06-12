---
title: "Best Partitioning Technique For Ubuntu???"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by vipin on 2008-01-23
What is the best way to install Ubuntu?

I have a 9 GB partition available for installing Ubuntu, and a live CD of Ubuntu 7.10i.

Right now I have installed it using these settings:---

ext3 file system with mount point "/" and a size of 2500MB
swap file system with 750 MB Size (my RAM is 384MB)
ext3 file system with the remaining space and a mount point of "/boot"

Right now its just finely installed, but the thing I want to know if I have done it correctly e.g is devoting around 5400MB space for "/boot" is ok or not? What about /home and other mount point partitions??? Right now I haven't set any partition size for them.

Pls tell me what should be the best way to install it by manually editing the partition table.

I will need it only for study purposes and may need to install Vanilla Kernel (as our case study) and some other things like MP3 Player for playing mp3 and etc...

thanx in advance,
vipin

---

### Post by gn2 on 2008-01-23
With only 9gb available for Ubuntu, set swap to RAM x 1.5 = 576mb and use all of the rest as "/" ext3.

This will make best use of the available space without wasting any.

---

### Post by vipin on 2008-01-23
what about the mount point???
should it be "/" or something else like "/home" etc.

Although I can see that it has created itself /home folder with a size of 324MB when I have allotted 2500MB for ext3 file system with mount point of "/".

So, all the space to ext3 with mount point "/" and 750 MB with swap is fine?

---

### Post by kellemes on 2008-01-23
> **vipin said:**
> what about the mount point???
should it be "/" or something else like "/home" etc.

Although I can see that it has created itself /home folder with a size of 324MB when I have allotted 2500MB for ext3 file system with mount point of "/".

So, all the space to ext3 with mount point "/" and 750 MB with swap is fine?


You only need a swap and a /(root)-partition
A /home-partition can be handy in some situations but it's not needed at all.
My /home is in general much smaller as /(root) since I use /home basically only for what it's primarily meant for.. user configuration data.
But this all depends on how you're going to use the system..
/boot is not needed also..

So.. one option would be..
swap 750Mb is fine.
/ 5G
/home the remainder

[B]or
[/B]swap 750 Mb
/ the remainder

Edit: Like I said, this depends on how you use the system.. so experiment a little, see how fast you're partitions fill-up, work with it and monitor your partition-space. This will give you an idea on how you can best partition your system next time. ;-)

---

### Post by bwtranch on 2008-01-23
You should have a /boot but that logical part only needs to be 512.

---

### Post by kellemes on 2008-01-23
> **bwtranch said:**
> You should have a /boot but that logical part only needs to be 512.


No reason for /boot

---

### Post by kellemes on 2008-01-23
Some more reading..
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by vipin on 2008-01-24
Yes, /boot partition is definitely needed. 

I dont know why, but when I installed it using swap of 750MB and ext3 of 2500 MB my computer failed to boot, its gave me an error:--

GRUB Loading Error
Error Code 5

Then I realised that maybe /boot has something and then I devoted the rest size to it and my computer booted without any problems.

But I dont know how much size is necessarily required for this partition. Maybe 512MB is fine, but I really dont know if this is true. If that partition is going to hold only boot information, then it should not get more than 2MB size, but I dont know what's wrong here!!!

---

### Post by Archmage on 2008-01-24
Modern computer don't need a /boot at all. And 5,400 MB is HIGHLY oversizes.

50 MB would be highly okay. 100 MB would be good for thoes that want to be 100% sure.

I would suggest to have a seperate partition for /home that has a desecent size (5 GB?). Than you can reinstall your whole system and format all partitionen but the /home and than you wont lose your user data.

---

### Post by Partyboi2 on 2008-01-24
If you are planning to compile kernels you will need to make sure you have enough room in / to compile the kernel. I agree that a /boot is not needed. Also don't forget to make use of the resize tool that comes with gparted.
and if you are interested the grub error 5 means
> : Partition table invalid or corrupt This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad signYou can read more [here.]("http://users.bigpond.net.au/hermanzone/p15.htm#5_")

---

### Post by vipin on 2008-01-25
So I am going to set this today:---


ext3 file system with / mount point 4000MB
swap with 750MB
ext3 file system for /boot with 100MB size
ext3 file sytem with mount point /home for the rest space...


i hope it will work just fine,,
thanx
vipin

---

