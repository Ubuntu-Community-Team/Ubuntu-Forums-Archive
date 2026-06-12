---
title: "Installing Ubuntu on a partition"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Penwin on 2010-01-14
Hi, I'm having a bit of trouble installing Ubuntu. I have two harddrives - a 260GB which I use for Windows, and a 1TB which I've partitioned into 900GB and 80GB partitions. I'm using the 900GB for storage, and was hoping to use 80GB partition for Ubuntu. When I open the installer on the CD it eventually asks whether I want to use the entire harddrive for Ubuntu and just switch between the partitions, or configure the partitions manually. If I use the entire harddrive I have to wipe it completely (which I can't do, considering there's about 300GB of important data on it). So I tried configuring the partitions manually but it says something like there's no "root system specified" (I have no idea what that means).

Is there a way to install Ubuntu on the 80GB partition without formatting the entire harddrive?

Any help would be much appreciated thanks.

---

### Post by darkod on 2010-01-14
I assume you created the 900GB and 80GB partition from windows. NEVER create partitions for ubuntu from windows, it doesn't work on ntfs.

Boot your windows and delete the 80GB partition. Leave the space as unallocated after you delete it, DO NOT create any partition.

Boot with ubuntu cd, select Install Ubuntu and tell it to use Largest Available Free space. It will set itself up in the 80GB space creating a default setup with root and swap partitions. If you want specific setup you need to use manual partitioning but you seem inexperienced for that.

The message you got is because you are trying to proceed with no root partition defined. It will not simply take the ntfs partition you created.

PS. If ubuntu installer does not offer the Largest Free space option because it has the other hdd selected, then just temporarily select the Erase and use whole disk option (even if you don't plan on using it), that will activate the drop down list beneath it, select the 1TB disk there and then again change the option to Largest Available Free space.

---

### Post by Geffers on 2010-01-14
> **Penwin said:**
>  So I tried configuring the partitions manually but it says something like there's no "root system specified" (I have no idea what that means).

Any help would be much appreciated thanks.

From memory just select the 'back' button then insert / (forward slash) where is says something like 'mount root partition.

I've done this accidentally before :D

Obviously when inexperienced with Linux the best way is to use a disk with no important data on it but probably the easiest way is to follow 'dakod's' method.

Geffers

---

### Post by nothingspecial on 2010-01-14
Firstly, 6-8 gigs is plenty for ubuntu itself. If you are planning to access all your stuff (music, documents, photos etc) from both os then you don`t need such a huge partition for Ubuntu.

When you get to the partitioning bit in the install process, choose manual (advanced). From the list of available partitions select the 80 gig one and right click on it, choose change (or use or whatever they call it nowadays).

Choose to use it as an ext4 journaling file system.

Set the mount point as /

Check the format box.

[COLOR="Red"][SIZE="3"]Do not touch the other partitions and do not choose the wrong one[/SIZE][/COLOR]

---

### Post by darkod on 2010-01-14
> **nothingspecial said:**
> Firstly, 6-8 gigs is plenty for ubuntu itself. If you are planning to access all your stuff (music, documents, photos etc) from both os then you don`t need such a huge partition for Ubuntu.

When you get to the partitioning bit in the install process, choose manual (advanced). From the list of available partitions select the 80 gig one and right click on it, choose change (or use or whatever they call it nowadays).

Choose to use it as an ext4 journaling file system.

Set the mount point as /

Check the format box.

[COLOR=Red][SIZE=3]Do not touch the other partitions and do not choose the wrong one[/SIZE][/COLOR]

This would work but it would leave the OP without swap partition (yes, I know you could set up swap file too). That's why I suggested deleting the partition and just letting ubuntu create its default root+swap routine.

---

### Post by nothingspecial on 2010-01-14
> **darkod said:**
> This would work but it would leave the OP without swap partition (yes, I know you could set up swap file too). That's why I suggested deleting the partition and just letting ubuntu create its default root+swap routine.

Of course you are quite right. I forgot about that bit. 

All my boxes are dual boot but they all dual boot linux, when I install the swap partition is already there.

@ Op - before my original instructions, you have to resize the 80 gig partition to leave an empty 2-4 gig partition which you assign to swap in the same manner I posted earlier.

But darkod`s way is probably easier if you`ve never done this before.

---

