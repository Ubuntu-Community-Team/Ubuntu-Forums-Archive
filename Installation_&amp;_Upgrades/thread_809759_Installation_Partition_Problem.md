---
title: "Installation Partition Problem"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by ahmedh on 2008-05-27
Hi, I am having a problem partitioning my hard drive for an Ubuntu installation. Currently, I have a ~7GB partition with my Windows installation (which is almost completely full) and a ~190GB partition on which I keep my files, music, movies, etc. This has 70 contiguous gigabytes free at the "end" of this partition (I used a defrag tool to create this large amount of continuous space). 

When I boot from the Ubuntu Live CD and attempt to install, I am greeted with three options: Use the entire disk (without any mention of either partition-it lists the disk as 200GB, the total of the two partitions), use the largest amount of free space (which should work--I have 70GB free and continuous), and manual. The "free space" option gives an error that I don't have enough free space. I don't want to use the entire disk, erasing both partitions and windows. And when I select manual, it doesn't give me any options except to create mount points. I can't make a new partition with my free space. This dialog does show my partitions, though.

When I open GParted, from the live environment, I can see my small Windows partition and I am able to edit it. I am not able to edit the larger partition, it simply won't let me. When I mount this partition, it appears like I would be able to change it, perhaps setting aside my 70GB, but a lock icon appears next to its name and I can't do anything at all. Below are screenshots of each situation, unmounted followed by mounted.

Any help would be greatly appreciated.

---

### Post by forestpixie on 2008-05-27
Are you not able to unmount your sda5 - I guess you were looking in there while in the livecd, what would make it mount.

Try to right click sda5 and unmount - then you should be able to work with it.

I would make 3 partitions , one for root (/) , one for home and one for swap.

No more than 10Gb for the root should be sufficient, maybe 10Gb for a /home and then a swap - that needs to be no more than 2xRAM. Leave the rest as it is in the partition you will be able to use it inside ubuntu - I would also be a bit worried about the win size as well.

When you then get to the partition part of the install you can pick the partitions you made for / and home and give them mountpoints of / and /home

Hope that helps some and is probably more than you were asking but I'm in verbose mode :)

---

### Post by ahmedh on 2008-05-27
Yes, that's from the LiveCD. I can unmount the drive, but I still cannot partition it :/

---

### Post by Pumalite on 2008-05-27
Try Gparted Live CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
(works with unmounted drives/pàrtitions)

---

### Post by forestpixie on 2008-05-27
> **Pumalite said:**
> Try Gparted Live CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
(works with unmounted drives/pàrtitions)

+1 - sort of ;)

I had some problems with gparted a while back - it wouldn't work/boot with any options on a few pcs I work with, ended up with partedmagic.

Don't know if there have been any recent changes to gparted, too lazy to look :)

---

### Post by Pumalite on 2008-05-27
Gparted-Live-0.3.7-2.iso should offer no problems.

---

### Post by ahmedh on 2008-05-27
I think my problem may be impossible to solve, actually...I tried partitioning with the Kubuntu live cd and qtparted, same sorts of failures. I tried the Partition Logic LiveCD and it wouldn't even recognize my harddrive. I guess I'll have to use Wubi, and be thankful that I can use my drive in Windows.

Thanks for all your suggestions.

---

### Post by forestpixie on 2008-05-27
Can i just ask - you are trying to resize the right partition aren't you - the extended can't be resized first you have to resize the logical within it.

---

