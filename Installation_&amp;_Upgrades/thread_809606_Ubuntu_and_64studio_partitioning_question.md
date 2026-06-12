---
title: "Ubuntu and 64studio partitioning question"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by nlz on 2008-05-27
I want to install 64 studio next to Ubuntustudio since the first one seems to be much more stable for live audio performance.

I'm having four partitions right now:
sda1 /root
sda2 /swap
sda3 /
sda4 /home

now i wanted to free up some space from /home to create a new partition but that seems so be very difficult because there are only four partitions allowed. 
I want to have something like:
sda1 /root
sda2 /swap
sda3 /ubuntu studio /
sda4 /home
sda5 /64studio /

But then i need to do stuff with and logical and primary partitions. The Gparted liveCD won't work because he doesn't recognize any screen (probably a problem with my Nvidia Geforce 8400) so I'm probably going to reinstall everything.

* Can I use primary and logical partions for everything (say home as logical)
* Should i have a seperate /boot partition for the dual boot?
* Can is access my /home ext3 partition from both of the operating systems? I will make two /home's, but i want to access them both from the different operating systems. Or should i then create a loose fat32 partition?

---

### Post by dstew on 2008-05-27
If you want more than four paritions, you need to create an extended partition into which you will put any number of logical partitions.

You can use primary and logical partitions for everything in Ubuntu. I think Windows wants to be on a primary partition, but with Ubuntu any kind of partition is OK.

You can have one /boot partition for both distributions, since the kernels will have different roots, they will not interfere. And, you can have one grub menu that way. Your distributions can also share a swap partition. Only the / (root file system) has to be separate for each.

You can have one /home partition for both systems, but you should use a different username for each, because your config files will be different in each system. If you want one common directory for data, you can create links to it in the home folders of each user. That way, you can have different config files, but use the same data files.

---

