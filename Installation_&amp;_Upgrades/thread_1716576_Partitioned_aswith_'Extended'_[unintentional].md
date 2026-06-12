---
title: "Partitioned as/with 'Extended' [unintentional]"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by stanz on 2011-03-28
I've split my 250GB HD on this Dell Laptop.
Lucid is first, has sda1 label, and I just put Maverick on the remaining free space.
The 10.10 iso was downloaded 2 days ago.

Please have a look at the attached screenshots, which read & show disk usage--in their own way?

I've not seen gparted or the disk utility show this before. I did not choose 'extended'
partition-during install.

This is the 2nd time, for this result...a bug?

Need any other info?

Thx in advance.

---

### Post by coffeecat on 2011-03-28
Is there a problem? :) Logical partitions inside an extended partition give you more flexibility, allowing you to exceed the four primary partition limit.  You need an extended partition as a "container" for logical partitions. Since Linux, unlike Windows, can boot from either primary or logical partitions, it doesn't matter whether your Ubuntu partition is primary or logical.

Bug? I doubt it. You don't say which option you chose during the install, but I guess the installer partitioner is set up to create logical partitions whenever possible. That's  a good thing, imo.

---

### Post by stanz on 2011-03-28
Hi,
Problem? I really don't know that much, to say that--but it is unexpected.
I've partitioned for testing and such, re-partitioned for years...without this type of result.
I always choose manual partitioning, but haven't learnt or needed to work with 'extended'.
Is this the option you mention?

Adding up the numbers threw my concern, so I figured to bring it up here.
Mainly I'm surprised, this is the first time the partitioner did something different like this.
I just had lucid & 2 separate partitions of natty on here [3 in total]...no results like this.

A good thing? I guess...it does boot and work, so thats kewl.
Thx for the quick reply, I hold back on re-installing!
:)

---

### Post by coffeecat on 2011-03-28
I don't know what the installer does when you create partitions in the "manual" option, but if you use Gparted before starting the installer, you have complete control over what partition types you want. I like to use Gparted before starting the installer and then use the manual/advanced option and simply point it at the partitions I've already created. 

You may know most of this, but it's a useful one for your bookmarks:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good luck with those logical partitions! :)

---

### Post by stanz on 2011-03-28
I hear that!
Yes - GParted, Used that for years and as you've said - used it to create the partitions I want the install on.
Thats my surprise - to find my partition changed to extended, and also to have 1MB unallocated, towards the end.

I'll check out the link, Thx coffeecat

---

### Post by srs5694 on 2011-03-29
Don't worry about the unallocated 1 MiB. That's probably a rounding issue to do with the change from "cylinder" alignment to 1 MiB alignment. (The policy for partition alignment has changed in recent versions of GParted and similar tools, in order to catch up to the modern state of hard disk technology, vs. where it was 20 or 30 years ago.)

---

### Post by stanz on 2011-03-29
Thx for the info srs5694, I got allot of catch-up reading to do--with new changes I notice.  ;)

---

