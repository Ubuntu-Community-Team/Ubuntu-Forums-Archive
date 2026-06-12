---
title: "[SOLVED] Moving from Dual boot to Ubuntu only"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by dlmoak on 2008-03-24
I recently installed Ubuntu 7.10 by downloading a version that automatically created a partition for itself on my hard drive and set up the dual boot option.  My main question is, if I decide to use Ubuntu instead of Windows, as I imagine I will, is it possible to tell Ubuntu to take over the entire drive or do I have to format the entire drive and reinstall?  I had to make some command line edits and download a driver or two to get all of my hardware recognised and would not like to have to do that again.  

Thanks in advance

---

### Post by scramasax on 2008-03-24
If space is getting tight, why not just shrink the partition?

Just install GParted, then access it from System > Administration >  Partition Editor

---

### Post by dlmoak on 2008-03-24
Thanks.
Space isn't the issue.  I'm wondering, if I want only one partition, if I need to install Ubuntu from scratch or if there is some way for my current installation to use the entire drive.

---

### Post by zvacet on 2008-03-24
@** dlmoak**

It is good thing to have separate home partition.You can make it following [this](http://www.psychocats.net/ubuntu/separatehome) guide.If you decide to delete windows you can add that space to your home partition or something else(depends what you want/need).

---

### Post by chex_m8 on 2008-03-24
There is a nice little utility called gparted that can help you. it's a live cd that you boot to and you can use it to shrink, and expand partitions without destroying them, So all you would do is delete the partition where windows is, then expand the partition that has ubuntu on it. Now as long as you are in gparted you may as well make a swap partition if you have not already. it only needs to be about 2GB in size and is used for virtual memory.

---

### Post by dlmoak on 2008-03-24
That sounds like the perfect solution.  Thanks so much.

---

### Post by dormant on 2008-03-24
gparted is a package in 7.10 - just add it using synaptic and then you can use it to fiddle with all your drives.

I haven't booted my machines into Windows for almost a year now. But I decided to keep the dual boot for the now incredibly small probability that I might come across something that I can only do in Windows.

---

