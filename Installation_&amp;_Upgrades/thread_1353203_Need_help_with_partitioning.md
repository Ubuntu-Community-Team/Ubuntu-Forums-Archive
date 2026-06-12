---
title: "Need help with partitioning"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by srbarry on 2009-12-12
Hi folks,

I need some help with installing ubuntu 9.10.  I've done a few ubuntu installations adding ubuntu too existing windows xp installations by simply using the automatic partitioner to create a ubuntu partition out of the existing swindows xp partition.  No problems.

I recently did a fresh install of windows xp sp3 on my system.  I have a single 160gb hard disk and when I did the xp install I created two partitions on the hd.  The first was a 150gb ntfs partition (C:\) to be used for xp and a 10gb partition (D:\) that I planned to use later to install ubuntu 9.10.  I hoped that this would be a cleaner way to go.  I finished the xp installation without any issues.

Now it's time to install ubuntu, but I'm a little unsure about using the partitioner.  I thought I could just choose the d:\ partition but things are a little more complicated than that.  The automatic partitioner assumes I was to divide up the c:\ drive which is not what I want.

So I guess I need to use the manual partitioner which I have not done before.  The paritioner shows two partitions:

device             type mount point  format?   size           used
/dev/sda
     /dev/sda1   ntfs                                   152044mb  8974mb
     /dev/sda5   fat32                                 7945mb      33mb
      free space                                          8mb

So, how do I proceed?  My best guess is to select the sda5 partition, use as 'ext3', select 'format' the partition and select / as the mount point, but I guessing here.  sda5 is now shown as a type ext3 and has / in the mount column.

I then get a message saying I have not selected a swap space.  Now I'm beyond guessing and don't want to proceed any further until I get some guidance.

Can anyone walk me thorough using the d:\ (sda5) drive for ubuntu, creating a swap within d:\ as well.  Of course without destroying the xp system on c:\ which took a long time to get right.

Thanks,

Steve

---

### Post by darkod on 2009-12-12
Creating a partition (D:) for ubuntu from windows seems to be common mistake. First of all it will be ntfs which ubuntu doesn't use. Second, the installer can't know why is it there and doesn't want to risk your data by deleting it, so it just considers it as unavailable space. What you need before starting the installer is unallocated unpartitioned space.
So the first step is to go into XP again and delete that second partition. And by the way, 10GB is quite small. It should be OK at first if you just want to see how it goes.
After deleting that partition and creating unallocated space, you have two ways to proceed.
Telling the installer to use Largest Continuous Free space, and it will set up ubuntu in it, or manual partitioning if you still want to do it. In that case, leave 1GB or 2GB for swap, and calculate how much remains for / from the unallocated space. Then:
1. Create logical partition, size as described, ext4, mount point /
2. Create logical partition, size 1GB or 2GB etc, swap area, mount point swap

That's it.

---

### Post by Bartender on 2009-12-12
> **darkod said:**
> 10GB is quite small. It should be OK at first if you just want to see how it goes.

+1
I was thinking the same thing.  10GB is OK if you're just experimenting I guess but won't do if you start using it and storing pictures, music, etc.

---

