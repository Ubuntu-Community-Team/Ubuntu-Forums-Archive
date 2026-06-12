---
title: "How do I install Ubuntu / Kubuntu on a specific drive"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by empire_a on 2008-08-18
Good day to you all,

Im a **complete** newbie to Linux so I would **really** appreciate some help as I would eventually like to be working completely on a Ubuntu system (sorry if this has been posted before, I did try to search the forum). 

I would like to install Ubuntu or Kubuntu from a DVD that I got with Linux Magazine - August 2008. I tried to install Kubuntu off the DVD (running through live Ubuntu using some program called VirtualBox)and I had no success as I could not select a drive where to install it (I dont know why?) 

MY COMPUTER SPECS
HP Pavillion DV9000, Vista, that has 240GB space on it (2 x 120GB hard-drives). 

The **first** hard-drive (BASIC HARD DISK 0) is 120GB and is used for my Vista C:\ 106GB and the Vista/HP Recovery E:\ 6GB - which I would like to leave as is.

The **second** hard-drive (BASIC HARD DISK 1) is 120GB and is used for my other documents. This drive has 3 partitions comprising of the following: ***D:\*** 23.4GB, ***F:\*** 44.2GB and ***L:\*** 44.1GB. I have backed up all my info, so I can afford to lose it.

I would like to install either Kubuntu (first option, from the DVD) or Ubuntu (second option , also from the DVD) to my **L:\**. I have no idea how to select the **L:\** for the installation. I tried to used the "Manual" installation step, but I read that the "Manual" option is for intermediate to advanced Linux users. When I tried, I got an error "the root system..."

I purchased Paragon Partition Manager if that helps? 
I would also like to have a "Dual Boot" option where I can choose either Vista or Kubuntu or Ubuntu (which ever one I can install)

I would appreciate some help or even a link to a post where I could read about the problem in question.

Best Regards,
A

---

### Post by rohedin on 2008-08-18
OK then, luckily your hard-drive is already partitioned, that should make things a bit easier.

With the manual option selected you should be presented with a graphical layout of your hard-drive setup. 

Since you have two hard-discs, you will most likely have sda for your first HD and sdb for your second. In those you'll have the partition number, so sda0, sda1, sdb0 etc. 

You'll want to work with the last partition of the second hard-drive if you want to install onto L:. Now, I haven't installed Ubuntu in a while so I'm not sure about all the buttons and thing, but here's what you do:

1) If you have free unpartitioned space in your Hard-Drive, create a 1gb partition there. If not then you have to shrink the last partition and then create the 1gb partition. 

2) Now select the BIG 44gb partition that was already there. You have to edit it's properties and set the filesystem to ext3 and then set the mount point to '/' without the quotes. This will act as the normal hard drive. Now we need a swap partition which is the 1gb partition you just made. Select the filesystem type as swap and you shouldn't need a mount point.


That should be it, like I said it's been a while since I've install Ubuntu/Kubuntu so maybe if somebody could back me up and what I've said here.

Good luck!


EDIT:

I recommend you look at this video before you go ahead, it should explain a lot of what I just said:
[http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1](http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1)

it is using an older version of Ubuntu, so it may look different but the general idea is still the same

---

