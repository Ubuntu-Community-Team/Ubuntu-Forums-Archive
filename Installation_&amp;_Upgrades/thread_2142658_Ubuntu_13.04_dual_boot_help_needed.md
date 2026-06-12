---
title: "Ubuntu 13.04 dual boot help needed"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by errolgreer on 2013-05-06
I have 2 hard drives, the first has Win 7 and Win 8 partitions in a dual boot arrangement.
The second HD has a partition for system image backups, and 9GB of unallocated space.

I have been trying to install 13.04 into the unallocated space. It offers to install 13.04 "alongside win 8" but I want it in the 9GB empty space, so I select "something else".

When I try to install, and select the 9GB space, it says I must first set up a partition.

Please give me step by step instructions to do this. I have tried but am not getting anywhere. I even went into Win7 and used a third party Partition Wizard to create Linux swap space and EXT4 partitions in the 9GB space, but I still cannot get 13.04 set up.

Many thanks

Errol

---

### Post by darkod on 2013-05-06
So right now do the created partitions exist or not?

When it said you need to create a partition did you try creating one?

If the swap and ext4 partitions still exist, in the Something Else option in the partitioning step, select the ext4 partition and hit the Change button below. Select the Use As ext4 (this is how you select the filesystem), mount point / and tick the format box.
Then select the swap partition and for Use As select swap area. swap doesn't use mount point so you will see the field greyed out.

That's it, continue the install and it should be OK.

But before you start, are you running UEFI on your system or not? Installing ubuntu might be different depending on whether you have uefi boot or legacy boot.

---

### Post by Hodevah on 2013-05-06
In addition to what Darkod says. Here is some additional information to help you alonlg. 

What you are wanting to do is triple-boot a system. Which is quite easy. I will try to lead you through this. 
What you need to do is when you install Ubuntu from the CD, it will usually offer you to opportunity to install it alongside or something else.* Something else *is what you need to choose. 

Go to the very, very top of GUI. Select **/dev/sda.** 

DEVICE FOR BOOTLOADER INSTALLATION needs to be **dev/sda.** _NOT_ _dev/sda1_ or _dev/sda2_ or anything like that. 
**dev/sda **is at the very, very top of the partition options in the GUI that  you will be given. 

Go to the free space you want to install Ubuntu on. Select it. You will get a pop-up dialogue window called CREATE PARTITION

Create a new partition using EXT4 or 3>TYPE FOR THE NEW PARTITION: Logical

NEW PARTITION SIZE: Select your size. Reserve some space for the needed SWAP space. Leave about 2X the amount of RAM your computer has. For example, 2 Gigs, then you will reserve 4 Gigs for SWAP. You might need to shrink Windows partitions to do this.
 
MOUNT POINT: /


You will also need to build a SWAP space as well. Very easy to do.  I will try to explain this as well. 
The other free space which you will need as SWAP space you will select as follows (you will need to have this partitioned beforehand or can do this through the partitioning GUI which you are/will be presented with;

USE AS: SWAP
MOUNT POINT: SWAP

---

### Post by errolgreer on 2013-05-08
Will give it a go and come back if necessary!
Thanks

---

### Post by errolgreer on 2013-05-13
Thank you, I have it loaded!

---

