---
title: "How many unallocated partitions do I need to Install Ubuntu?"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by reeegiii on 2012-01-19
This will be my first time installing Ubuntu on my laptop. I have read some tutorials but I'm still confused on dealing with my partitions. 

I currently have 4 primary partitions: System, C:, Recovery, and HP_Tools. I'm planning to delete the "Recovery" partition, since I already have my recovery disks, which would leave me with 3 primary partitions. 

I have read that when I install Ubuntu I'm going to end up with 2 more partitions: The root partition and the swap partition, which would give me all in all 5 partitions, but I have read that I can't have more than 4 primary partitions. 

So, do I need to delete one more primary partition to give way for the partition that Ubuntu will create?

---

### Post by cortman on 2012-01-19
> **reeegiii said:**
> 
So, do I need to delete one more primary partition to give way for the partition that Ubuntu will create?

Yes. The max number of primary partitions on an HD is 4. What is the nature of HP_Tools? Sounds like some kind of bloatware partition to me.
You'll want to install the Ubuntu system on the new primary partition. Set the mount point for that partition to " / ", for the root file system.
Whether or not you create a separate partition for your /home (which is where all your user configuration files, plus all your personal files are saved) is up to you; I would recommend it, personally.
For the swap partition and any others you want to make, I would recommend creating an "Extended" partition, which basically is just a container partition in which you can create an unlimited number of "child" partitions.
I hope this helps some. There are quite a few partition gurus on these forums, so feel free to ask any questions!

---

### Post by deonis on 2012-01-19
You do not need to worry about the partitions .. but you are right for the number of primary ones. Just free some space about 50-70 Gb (it could be as small as 2Gb). Try installing Ubuntu 10.04. When you will be partitioning your disk click of the link for the custom partitioning and create the following 4 partitions: 

/boot (Ext3)
/ (root) (Ext4)
/home (Ext4)
/swap (swap)

it should be it ... some people also suggest to make /tmp partition but it's up to you.

good luck!

---

### Post by ajgreeny on 2012-01-19
You can make one extended partition in place of the one you delete, and can then make new logical partitions within that extended partition for all the ubuntu partitions needed;  even root partitions of linux distros can be logical.

So delete the recovery partition, if that is your decision, (will it be big enough?) and then either use the "Something else" option when installing and use the free space to install everything in logical partitions, or use gparted on the live CD/USB system to make as many logical partitions as you want in the free space before installing.  You will still need the "Something else" option in order to use existing partitions at installation.

---

### Post by reeegiii on 2012-01-19
> **deonis said:**
> You do not need to worry about the partitions .. but you are right for the number of primary ones. Just free some space about 50-70 Gb (it could be as small as 2Gb). Try installing Ubuntu 10.04. When you will be partitioning your disk click of the link for the custom partitioning and create the following 4 partitions: 

/boot (Ext3)
/ (root) (Ext4)
/home (Ext4)
/swap (swap)

it should be it ... some people also suggest to make /tmp partition but it's up to you.

good luck!


Just so you know, I have the Ubuntu 11.10.

You said that I should free a 50-70 GB partitions, is that a single unallocated partition? And will that cover up the /boot, /, /home, and /swap that you mentioned?

---

### Post by darkod on 2012-01-19
The size depends on the way you use your computer. Most probably you will have lots of data on C: too, so both windows and ubuntu can use it (otherwise windows can't read by default the ubuntu partitions). In that case, assuming all big files are on C:, ubuntu can fit on a partition as small as 6-8GB. The default install is around 3.7GB if I remember correctly.

Also, programs are not as space consuming as in windows.

/boot is not really needed, up to you if you want to create one. Size of 500MB is plenty for /boot.

/ also depends on how many and what programs you want to install, and whether you already know approx their size. / partition of 10-15GB is fine so that you have spare space.

swap partition is mainly used if you hibernate regularly. In that case it should be around 1.5 x RAM size which might be a lot if you have huge ram capacity. In normal use, the more ram you have, less chance of swap being used at all (I have never seen mine used on a desktop with 6GB). If not planning to hibernate you can make swap 2GB just in case you ever need it.

/home size will be the rest, from the space you want to allocate to ubuntu subtract the above partitions sizes. Again, if you plan to keep most huge files on ntfs so that windows can access them, a small /home will do it for you.

---

### Post by reeegiii on 2012-01-19
@darkod

I have a huge amount of unused memory but that's not really my problem. I need to know how many unused partitions (I currently have 4 primary) do I need to have to cover all the partitions needed for Ubuntu(/boot,/,/home, and /swap). I'm not asking the size of a partition, I'm asking for the count of partition.

---

### Post by darkod on 2012-01-19
> **reeegiii said:**
> @darkod

I have a huge amount of unused memory but that's not really my problem. I need to know how many unused partitions (I currently have 4 primary) do I need to have to cover all the partitions needed for Ubuntu(/boot,/,/home, and /swap). I'm not asking the size of a partition, I'm asking for the count of partition.

Well, the very minimum is / and swap. Just two.

As mentioned earlier, deleting one primary partition will allow you to create one extended which can contain many logical partitions inside.

If you decide to install with separate /home partition that makes the number of partitions 3.

You don't need separate /boot partition unless you are making some specific setup that needs it.

---

### Post by deonis on 2012-01-19
> **reeegiii said:**
> Just so you know, I have the Ubuntu 11.10.

You said that I should free a 50-70 GB partitions, is that a single unallocated partition? And will that cover up the /boot, /, /home, and /swap that you mentioned?

Sorry, I did not make it clear .. yes it's for all partitions. But as I said, it is up to you how much space you want to allocate for each partition ... my "Usual" setup is the following: 

/boot 500 Mb
/ (root) 15 GB
/home 35 GB (you can make this one bigger)
/SWAP - a size of your RAM or more

---

### Post by reeegiii on 2012-01-19
Edit post: Nevermind, everything's working fine now. Thank you.

---

### Post by mastablasta on 2012-01-20
you need only one and Ubuntu will make other necessary partitions automaticly.

---

