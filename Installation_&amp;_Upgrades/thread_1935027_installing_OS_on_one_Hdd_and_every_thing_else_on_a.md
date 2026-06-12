---
title: "installing OS on one Hdd and every thing else on another"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by Borunco on 2012-03-03
Hi, i came across a post that you could put the OS on one Hdd (like ssd) and every thing else on another like /Home etc.
dose any one know where to find that post. I have been trying with no success.
How do I do that in gparted?
I know how to do it with the same Hdd, but not with two.
any help is very much appreciated
borunco

---

### Post by darkod on 2012-03-03
When you say you know how to do it, you mean installing with the manual option? Because that is how you create separate /home partition.

There is no difference whether you use one or two disks. Specify the mount point / for one partition on one disk, and /home and swap to another disk, or where ever you want. Specify to install the bootloader where you want it.

That's it.

---

### Post by Borunco on 2012-03-03
> **darkod said:**
> When you say you know how to do it, you mean installing with the manual option? Because that is how you create separate /home partition.

There is no difference whether you use one or two disks. Specify the mount point / for one partition on one disk, and /home and swap to another disk, or where ever you want. Specify to install the bootloader where you want it.

That's it.

Ok, thanks I can do that, I didn't know that it would be recognized like that.
Thanks, Darkod

---

### Post by darkod on 2012-03-03
With the manual option you will have all disks and partitions listed. Of course you can also create new partitions from unpartitioned space.

So, there is no limitation setting root on one disk, and /home on another, etc.

---

### Post by Borunco on 2012-03-03
> **darkod said:**
> With the manual option you will have all disks and partitions listed. Of course you can also create new partitions from unpartitioned space.

So, there is no limitation setting root on one disk, and /home on another, etc.

Do you recommend setting root and swap on the same disk, or dose it matter in terms of how the computer will see it, or over all boot speed?

---

### Post by darkod on 2012-03-03
The good point with linux is that it doesn't care. Similar to the choice whether to have a separate /home partition or not.
If you don't, your Home folder is inside root with path /home.
If you do, your Home folder is on a separate partition again with path /home.

It doesn't care.

But if you do want to use swap, and since you mentioned SSD, it's better to set swap on a HDD. Or don't set it up at all if you have enough RAM and no HDD available.

Whether you want to set /home on the ssd or hdd is up to you.

Setting up root on the ssd will definitely make it work faster.

I'm no expert, the above are a few basic rules I know since I'm saving for a sdd too.

---

### Post by Borunco on 2012-03-03
> **darkod said:**
> The good point with linux is that it doesn't care. Similar to the choice whether to have a separate /home partition or not.
If you don't, your Home folder is inside root with path /home.
If you do, your Home folder is on a separate partition again with path /home.

It doesn't care.

But if you do want to use swap, and since you mentioned SSD, it's better to set swap on a HDD. Or don't set it up at all if you have enough RAM and no HDD available.

Whether you want to set /home on the ssd or hdd is up to you.

Setting up root on the ssd will definitely make it work faster.

I'm no expert, the above are a few basic rules I know since I'm saving for a sdd too.

I installed a ssd on my net book (Acer Aspire One with 1 gig of ram) Running Lubuntu 11.10. From the time it lives bios post screen to the time I,m on INTERNET is 15 second. to me that is crazy, and you get really spoiled with that boot time. when i had a regular Hdd, it would take 45 seconds to boot. I love ssd drives.
Thanks for your help, I'm going to mess around with that partitioning on one of my test boxes. :popcorn:
borunco

---

