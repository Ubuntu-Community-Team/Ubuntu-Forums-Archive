---
title: "resize partition and create partitions from it"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by techbrainless on 2011-01-09
Hi All,

I have installed ubuntu 10.4 -  /home partition with 300GB , i have 90% of this partition free, is it possible to resize the /home partition and free some of it and recreate partitions from it..........

---

### Post by Quackers on 2011-01-09
Yes, it is possible to do that. As for advice, you will need to give more details. For a start, a screenshot of your gparted screen would be good.
If you don't have gparted (under System > Admin) you will need to first install it via synaptic package manager.

---

### Post by techbrainless on 2011-01-30
Hi [Quackers]("http://ubuntuforums.org/member.php?u=369240") ,

here is the gparted screen shot .

---

### Post by Quackers on 2011-01-30
According to your screenshot you don't have a /home partition, only Ubuntu root (/) partition of 460GB
If you want to resize sda1 you should boot from the Ubuntu live cd/usb and open gparted in that.
Then you should right-click on the swap partition and choose "swapoff".
Then right-click on sda1 and choose the resize option. You can then make the changes you wish to make, close the new window, and click on the green tick mark in the toolbar to apply the change.
Depending on what you wish to do with any new partitions you can create up to 2 more primary partitions in the resulting unallocated space. No more than 2 though!
If you want more than 2 new partitions, you should extend sda2 (the extended partition) to occupy the unallocated space, then you can create as many logical partitions as you wish within that extended partitions.
Please bear in mind that Windows cannot be installed in a logical partition.
(Well, it can be installed, but it won't boot!).

---

### Post by techbrainless on 2011-01-30
[]("http://ubuntuforums.org/member.php?u=369240")Thanks Quackers ,

> According to your screenshot you don't have a /home partition, only Ubuntu root (/) partition of 460GB
You are right I have only one partition which is /root

> If you want to resize sda1 you should boot from the Ubuntu live cd/usb and open gparted in that.
I did not think of using Live cd , really it is amazing idea.

I will do that and feed you back . Thanks alot

---

