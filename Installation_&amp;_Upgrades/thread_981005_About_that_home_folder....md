---
title: "About that home folder..."
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by Preserved_Killick on 2008-11-13
Hi everyone,

When I installed Ubuntu for the first time a year ago, I followed some instruction to create a separate partition for a home directory. I guess it worked.

Now, I'd like to install a fresh copy of 8.10 on a reformatted partition, but not loose anything in my home partition. 

Question is, how can I be certain that I've got the correct partition when it comes time to reformat?? I've got a partition with a Mountpoint of /home, but that's 186 gigs.  When I look at the properties of my home directory in Nautilus, it tells me that the total space is around 105 gigs. Nothing looks to be 105 gigs in Gparted? 

Here's a screenshot of Gparted:[IMG]http://picasaweb.google.com/lh/photo/UV_5c625lI-WTK7vgeXtUA[/IMG]

[http://picasaweb.google.com/lh/photo/UV_5c625lI-WTK7vgeXtUA](http://picasaweb.google.com/lh/photo/UV_5c625lI-WTK7vgeXtUA)

How can I be sure to protect my home partition when I can't even identify it? 

-Preserved

---

### Post by taurus on 2008-11-13
/dev/sda3 is your /home partition.

---

### Post by Preserved_Killick on 2008-11-13
> **taurus said:**
> /dev/sda3 is your /home partition.

So, I could be safe wiping out sda1 (windows boot partition),
sda2 and sda6..correct? 

What I'm looking for is no more windows partition, or that fat32 sharing partiton, I just want a basic single large partition for 8.10, keep my /home partition and the linux swap partition. Sound right???

---

### Post by taurus on 2008-11-13
You can use gparted from the LiveCD to combine both /dev/sda1 & /dev/sda2 into a single large partition.  And since /dev/sda6 is a logical partition, it's hard to combine that space with either primary partitions.  However, you can format /dev/sda6 to ext3 and have it mount to /usr unless you want to use that space as a storage or backup.

---

