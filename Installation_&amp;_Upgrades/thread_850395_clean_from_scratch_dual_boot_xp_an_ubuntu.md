---
title: "clean from scratch dual boot xp an ubuntu"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by drixomanbeta on 2008-07-05
Hi

I got a 320GB hard disk that i like to dual boot with ubuntu 8 and xp.  the disk is new so there is nothing on it... I plan to have the disk divide into the following:  

80GB XP,60GB ubuntu, 40GB ubuntu swap, 40GB XP Virtual RAM storage, and the rest just storage...

At first i tried installing xp but the installer only detect 1/3 of my 320GB hard drive...  I live-booted into Ubuntu and see it can detect the full capacity of the disk...  I don't know what the problem with xp installer but since i want to allocated only 80GB for xp installation i went ahead with the partition in xp setup and divided the xp detected portion into 1 80GB and some free space.   

Then I went into ubuntu but i am bit lost on the ubuntu partitioning process so please guide me through the ubuntu setup process with my existing xp...i am a total newb with linux stuff.

Thank you very much!

---

### Post by Partyboi2 on 2008-07-05
40GB ubuntu swap is to much, you will only need probably a couple of gig for /swap, roughly about x2 the amount of onboard ram.
When you get to the partitioning part of the installer, choose to use manual and create a ext3 /root partition for the system files, and a /swap partition. If you want to have your home folder (all your data)on its own partition then create a ext3 /home partition as well. This is useful if you need to ever reinstall in the future.
Ubuntu uses the ext3 filesystem but is able to read/write to ntfs, so maybe for the storage partition you can use ntfs so that both machines can access it as windows cannot read/write to ext3 unless you install a small program for windows.

---

### Post by raja on 2008-07-05
I find it useful to set up the systems separate from a data partition that can be shared. For example, I would used 10 GB for win XP, 10 GB for Ubuntu and a big data partition. The data partition could be formatted as NTFS and then accessed from both xp and ubuntu. You just will bever need that much swap. Set it to 1 or 2 GB. A separate /home partition is an option to consider too.
It may be easiest to boot up with the ubuntu live cd, create the partitions, then reboot and install xp and then install ubuntu.

---

