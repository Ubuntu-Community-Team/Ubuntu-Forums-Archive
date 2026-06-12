---
title: "Partition Layout for Win7 Dual boot 80GB drive"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by nismoz33 on 2011-03-20
I don't have much experience with Ubuntu.  I have played with the LiveCD but haven't gone through a full install process.

I have been searching & found the tutorials for a dual boot installation but the one thing I can't seem to find, is the best way to layout the partitions for my drive.

I have an 80GB hard drive that I will be using in an old laptop.  I will be running Windows 7 on this laptop & want to have Ubuntu 10.10.  

I would like to have a partition for my user files so they can be accessed from both Windows 7 & Ubuntu.

Can someone please help me with the best way to carve up my hard drive?

Can you specify what format each partition should be?  Also, does it matter what order the partitions are created in?

I was thinking about the following.

40GB for Windows 7
15GB for Ubuntu
4GB for swap 
20GB for shared user files

Am I missing a partition?  Does the above look OK?  Can I just create the 40GB partition for Windows 7 & install that & then let the rest get created during the Ubuntu installation?

Sorry for the newb questions but I have been searching for the last couple hours on this site & Google & can't seem to find a good solid answer.

---

### Post by Hedgehog1 on 2011-03-20
> 40GB for Windows 7
15GB for Ubuntu
4GB for swap 
20GB for shared user files

Your basic plan is sound.

For best results, use windows 7 to shrink & move Windows Paritions.

Use Gparted (**G**nome **PART**ition **ED**itor) to create Ubuntu partitions.

When you boot off the LiveCD/LiveUSB, you will find gparted in the menu at System >> Administration >> Gparted.

You will end up with 5 partitions (Windows 7 installs a small boot partition).

This means you will put the Linux partitions inside a single extended partition.

It will look like this (but with one more NTFS partition):

[IMG]http://img268.imageshack.us/img268/5948/small48gpartedview.png[/IMG]

***The Hedge***

:KS

---

### Post by nismoz33 on 2011-03-20
Hedge thanks for the response.  My one question I still have then is about the 20GB partition for the shared user files.  

What format does that partition need to be in?  Will Ubuntu be able to access NTFS partitions?

---

### Post by Hedgehog1 on 2011-03-20
> **nismoz33 said:**
> What format does that partition need to be in?  Will Ubuntu be able to access NTFS partitions?

Thanks for calling me Hedge.  I like that!

Yes, Ubuntu reads and writes NTFS partitions fine now-a-days.  So that shared should be NTFS.

You OK otherwise?

***The Hedge***

:KS

---

### Post by nismoz33 on 2011-03-20
I will start the process & see how it all goes.  I think for now this should get me started.

I'll report back if I run into any issues.

---

