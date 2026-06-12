---
title: "Installing Ubuntu 10.10 with only one free PRIMARY Partition?"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Panpandachan on 2010-10-12
Hey everyone.

So basically, right now I've been playing around with Ubuntu using Wubi and I would like to actually install Ubuntu onto its own partition. But I dont want to lose my Windows OS either (I need it for applications like MATLAB and LabVIEW).

My issue is, my laptop currently already has three primary partitions. One for windows, one for recovery and one "SYSTEM_DRV" (used to hold OEM windows license info apparently).

I dont want to mess with any of those partitions.

Anyway, my question is, can I still install Ubuntu when I only have one primary partition? 

I read about extended and logical partitions in the guide, but the wording was pretty confusing. All it said was Ubuntu needs two partitions, it didnt say if the partitions could be any type.

---

### Post by gyussz on 2010-10-12
You're right, Ubuntu needs 2 partitions, one for the system, and one for swap. This article about swap is quite clear in my honest opinion: [http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space).

By the way you can install it without a swap partition, but the system will crash very often if you run out of RAM, or during any other swapping process.

The only solution I can imagine is to shrink your Windows partition, and create the partitions that Ubuntu needs. You can shrink it with Gparted on the LiveCD, Windows 7 also has its own partition manager (but feel free to use anything else you trust). This won't affect the recovery, and the "SYSTEM_DRV" you mentioned.

Hope I could help!

---

### Post by ronparent on 2010-10-12
Your best bet is to use win 7 to shrink your windows partition. Then from a live cd use gparted to create an extended partition (which counts as one of your primary partitions but will keep your primary count to four primaries). You should then be able to install to the vacant space - the extended. Good lick.

---

### Post by Panpandachan on 2010-10-12
So if I'm understanding you guys correctly, here is what I can do:

1. Shrink my current windows partition using windows (tried it, says i can free up 88GB, not bad I guess)
2. Create a new (fourth) primary partition for Ubuntu
3. Then, I can create another extended partition from the new primary partition. Effectively creating a total of two new partitions for Ubuntu
4. I can use the extended partition for swap and the fourth primary for Ubuntu?

---

### Post by efflandt on 2010-10-12
Not quite.

1. Shrink Win7 or Vista from its own computer management.

Then because I have heard that 10.10 has no selection to install in unallocated space, and automatic partitioning may not create enough swap space to hibernate:

2. Create an extended partition (which counts as one of the 4 maximum primary or extended partitions).  You could use gparted from install CD booted to live system.

3. Then I would use gparted to create the "logical" partitions you want for Linux, at least one partition for the system (ext4 or ext3) and swap at least as large or slightly larger than RAM if you want to hibernate.

Then during installation use Advanced mode of partitioning to select the partition you created for Linux as / (root).  It will automatically find the swap partition.  Or if you created any other logical partitions like for a separate home partition you can assign that as /home.

Summary: You can only have a total of 4 "primary" or "extended" partitions with an msdos partition table.  But you can have any number of "logical" partitions within an extended partition.

---

### Post by Panpandachan on 2010-10-12
Alright that sounds good.

I'm in the process of removing my Wubi install and burning a Ubuntu 10.10 Desktop disk right now.

Cant wait to get this done.

Thanks a lot, you and everyone.

---

### Post by oldfred on 2010-10-12
Once you have shrunk windows reboot it a couple of times, so it has recognized its new size. It will run chkdsk and maybe other repairs.

If you are creating partitions, a slightly more advanced is a separate /home. That keeps your data separate from your system. Or you can create a shared NTFS partition for anything that you want in both windows and Ubuntu. If data is not in root or home then smaller root is ok. I have several / partitions that are 20GB with only 6GB used, but data mounted from other partitions.

I like the shared ntfs partition when you are first starting as you will boot into one or the other and spouse comes along and wants to check email which is in the other. I went and moved Thunderbird profile & Firefox profiles to shared NTFS partition so the two main apps had exactly the same data in both.

---

### Post by Slim Odds on 2010-10-12
> **gyussz said:**
> You're right, Ubuntu needs 2 partitions, one for the system, and one for swap. This article about swap is quite clear in my honest opinion: [http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space).

...

That article that you linked to also mentioned that you can use a swap **file **instead of a swap **partition**. It's not as efficient, but it works.

---

### Post by cthom on 2010-10-12
doesn't wubi just install ubuntu to a normal windows partion? i did this with lucid with no problems.

---

### Post by Panpandachan on 2010-10-12
oldfred, I was planning on doing something like that.

I was just going to use a folder in my windows partition to store all of my documents, music, etc (stuff that normally is in home). And then have only a root and swap partition.

Slim Odds, I noticed that too but I figure its best for me to just stick with a swap partition.


Hey guys, one last question, I just read this thread: [http://ubuntuforums.org/showthread.php?t=1592415](http://ubuntuforums.org/showthread.php?t=1592415)

And I'm wondering... is that an issue for me if I'm going to be doing this manually?

EDIT: cthom, yea it does. I meant I have Ubuntu installed using Wubi right now, and I'm uninstalling so I can install Ubuntu to its own partition. Sorry for being unclear.

---

### Post by Panpandachan on 2010-10-12
Wooh, everything is fine. Got it up and running within an hour and I've been playing around with it since.

Thanks again everyone :D

---

