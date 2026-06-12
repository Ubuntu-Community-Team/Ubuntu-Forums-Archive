---
title: "Newbie"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by tmh177 on 2008-06-17
1) I have a SATA, 160 gig HD, on it I have 1/2 the space partitioned for Vista, which is up and running, and the other 1/2 is unallocated. I tried to install Ubuntu last night and got to the partition part and noticed that Ubuntu was claiming most of the space, so I backed out. Is there a way I can install just using the unallocated space?


2) Is there a way to get the fire starter firewall offline?

3) also no clue on what prefex is for, I got following
"The following errors occurred with your submission:  
You must select a thread prefix". Please let me know, as new.
 


TMH177

---

### Post by ad_267 on 2008-06-17
When you install it you can use the manual option to select partitions.

You will need to open up the gparted partition editor first which is included on the live cd to partition the unallocated space as ext3 and also create a partition of around 1 or 2 GB formatted as a swap partition.

I think this is one problem with the current installation procedure as it doesn't allow you to select unallocated space, only resizing of an existing drive and it isn't often obvious what this will do if there are multiple partitions.

You can download the firestarter package from here: [http://packages.ubuntu.com/hardy/firestarter](http://packages.ubuntu.com/hardy/firestarter)
It is only a GUI front end for the firewall that is already installed by default.

The prefix thing is a new feature in the forums that makes it easier for people responding to know which type of ubuntu you're using as instructions would be different for ubuntu, kubuntu, xubuntu etc.

---

