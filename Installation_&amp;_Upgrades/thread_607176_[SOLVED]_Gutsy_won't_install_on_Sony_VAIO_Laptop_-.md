---
title: "[SOLVED] Gutsy won't install on Sony VAIO Laptop - Won't Partition HD"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by crjackson on 2007-11-08
Here's my problem.  I have UBUNTU on every system in the house now except my wife's laptop.  She finally got tired of windowsxp always screwing up and needing to be reinstalled, and has warmed up to the big U on the other systems.

I get the go ahead to make her lappy a dual boot, but I can't get U installed.  The live cd works PERFECTLY on her system.  Everything is recognized and works great.  The problem is that the install stops at the partitioning section.  It tries but stops and just says it can't partition the drive.  Nothing in the Ubuntu partition section can configure this drive.

Okay, I had a copy of GPARTED on CD and booted it.  It sees the HD no probem.  I make my selection for partition sizes and click apply.

It starts to do it's thing, then it stops.  It puts a yellow exclamation mark in the partition listing.  It doesn't give an error message.

I boot back into windows, it finds newly created error in the partition table and repairs them.  Then it boots as usual...


Where do I go from here?

---

### Post by bulldog on 2007-11-08
Did you defragment the drive several times before you try to resize it?
It's possible there are file chattering over whole hdd,which prevents Gparted to resize it.

---

### Post by crjackson on 2007-11-08
> **bulldog said:**
> Did you defragment the drive several times before you try to resize it?
It's possible there are file chattering over whole hdd,which prevents Gparted to resize it.

Yes, and all free space is consolidated.  The drive only has 26GB occupied.  It's an 80GB drive.  The end of the drive is nothing but free space.

---

### Post by bulldog on 2007-11-08
Maybe you can create some free space in windows?
Just giving some thoughts,not really knowing why it can't be done.

---

### Post by crjackson on 2007-11-08
> **bulldog said:**
> Maybe you can create some free space in windows?
Just giving some thoughts,not really knowing why it can't be done.

The drive already has 48GB of free space at the end of the drive.  I'm puzzled...:confused:

---

### Post by crjackson on 2007-11-08
I'm going to try an ofline system file defrag using Perfect Disk, then do an online defrag again.  I download a partitioning tool called [Parted Magic]("http://partedmagic.com/").  I'll try it next and see what happens...

I've done approximately 100 Ubuntu installs and most of them dual boot.  I've heard of similar problems but this is a 1st for me.

After looking at the partedmagic page, I see that it's just GParted in a different package.  Perhaps it's a newer version that what I had already...

---

### Post by bulldog on 2007-11-08
How is the disk partitioned at this moment?
Maybe you want to do something what isn't possible.
You can only have 4 primary partitions for that matter.
If you want to create more partitions you need to give up one primary and make ik an extended partiton.
In this extended partition you can create logical partitions.
You can install linux on logical partitions and make a swap as well,but you shouldn't install windows on a logical,just let it be on the first primary.

---

### Post by Pumalite on 2007-11-08
You can also try rescuecd: [http://www.sysresccd.org/Download.en.php](http://www.sysresccd.org/Download.en.php)
(it has a partitioner)

---

### Post by crjackson on 2007-11-08
> **bulldog said:**
> How is the disk partitioned at this moment?
Maybe you want to do something what isn't possible.
You can only have 4 primary partitions for that matter.
If you want to create more partitions you need to give up one primary and make ik an extended partiton.
In this extended partition you can create logical partitions.
You can install linux on logical partitions and make a swap as well,but you shouldn't install windows on a logical,just let it be on the first primary.

It only has a single NTFS partition for WinXP.  I wanted U to just do it's default install.

---

### Post by crjackson on 2007-11-08
> **Pumalite said:**
> You can also try rescuecd: [http://www.sysresccd.org/Download.en.php](http://www.sysresccd.org/Download.en.php)
(it has a partitioner)

I'll try that too and see what happens...

---

### Post by crjackson on 2007-11-10
Well, I downloaded the latest version of [partedmagic]("http://partedmagic.com/") and it got the job done without a hitch.  Wife is now duel booting winXP and Ubuntu Gutsy.

This thread is solved.

---

### Post by bulldog on 2007-11-10
Nice to hear it's solved :guitar:

[note to myself:take a look at partedmagic as soon as possible]

---

### Post by Pumalite on 2007-11-10
I already copied to my Tomboy.

---

### Post by crjackson on 2007-11-10
> **Pumalite said:**
> I already copied to my Tomboy.

Cool.  Maybe it will be useful to someone else too...

---

