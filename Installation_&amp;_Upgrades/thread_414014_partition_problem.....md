---
title: "partition problem...."
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by sobira on 2007-04-19
Hallo :P 
I am currently using ubuntu edgy , but i want to upgrade to feisty 
to make life a lot easier... i want to create a separate /home partition 
i tried following [this]("http://www.psychocats.net/ubuntu/separatehome") guide
with my edgy live cd , 
But there is a little problem ... after resizing my NTFS (windows partition ) to create /home partition .
I get an error "It is not possible to create more than 4 primary partitions"
[img]http://gindis-world.org/partitions.png[/img]
(image is from gparted in edgy not live cd )
i seem to have forgotten how to make it logical :oops: 
please help :( i am kinda still new to Ubuntu

---

### Post by bulldog on 2007-04-19
You can have only four primary partitions,you know this already.
But if you're willing to give one primary away,and create an extended partition of it which should be the size of the free space left,you can create numerous logical partitions in it.

Ubuntu doesn't care to be installed on a logical partition,windows however,wants to be installed on a primary,and to avoid trouble,I should recommend to us the first primary for it.

---

### Post by louieb on 2007-04-19
You already have an extended partition and two logical partitions. The problem is where the free space is  located. An extended partition and the logical partitions it contains have to occupy contiguous space.
If it were mine 
I would delete the swap partition freeing up hda3 to use.
Set up the 9+ gig unallocated space as hda3.
See if you can resize hda4 your extended partition, so that it contains the space in the old hda3 swap. 
If so you can then allocate the old hda3 space as a new logical partition for swap. 
If not then you'll just have to chop space off hda5 or 6 to create room for a logical swap. And if you want to reclaim the space formerly used by hda3 you can resize hda2 to use that space.

BTW: Because the partitioner cannot work on a mounted partition you will have to use a live CD. I suggest you get the GParted Live one.

another note you will also have to change /etc/fstab to reflect the new location of swap. (It could be ugly if you forgot that). :oops:

---

### Post by sobira on 2007-04-21
thanks for your help bulldog & louieb , but i decided to do a fresh install and setup a seperate home partition from the beginning  :) 
and resized the extended partition

---

