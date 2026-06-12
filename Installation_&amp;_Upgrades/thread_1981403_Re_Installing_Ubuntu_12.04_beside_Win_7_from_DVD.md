---
title: "Re: Installing Ubuntu 12.04 beside Win 7 from DVD"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by wildfire365 on 2012-05-15
I'd like to find out how to load Ubuntu 12.04 on my windows 7 computer I know I have to make a new partition but would like to find out how to do without loosing any of my files on windows and also I tried to load it on a windows computer by putting in the disk and wipe out windows and put Ubuntu only on it, but it wouldn't load I tried to boot off the disk to see it would kick in and start to format it but it wouldn't anyone can help I'd appreciate it alot thanks. wildfire365

---

### Post by zvacet on 2012-05-18
I don't know if you still have Windows installed,but read [this.]("http://www.psychocats.net/ubuntu/installing")

---

### Post by Mark Phelps on 2012-05-18
You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space. When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by fruiz002 on 2012-05-18
Hello,

I'm trying to setup a Paypal IPN system and when the remote server tries to read the files in my server it tell me that they can't be found in the following folder:
/var/www/dalohosting/signup-paypal/include/merchant/

Strange for me is that the Server refers to /var/www when it should refer to //host/dalohosting.. , right?

I would be grateful to get some help

Regards
PS: sorry if the post is not in the right place, I'm new...;-))

---

### Post by zvacet on 2012-05-18
@ **fruiz002**

Open new thread in general help.That way you will get answer faster and you will make problem you have transparent to others who have similar problems.Enjoy Ubuntu!

---

