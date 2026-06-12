---
title: "Partition Sizes."
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by abiss27 on 2011-04-26
Hey guys I made a partition of 105 GB unallocated space on my 320 Gb HDD  using  Windows 7 Disk Management, and i used this partition to install  Ubuntu 10.10 on it. But what I did not understand is when I was manually  doing the *partitioning* scheme using the  Ubuntu installer it  would show up as 112.7 GB. I also had to do a fresh install after that  and again I encountered the same thing, can anyone share some knowledge  on this?

---

### Post by coffeecat on 2011-04-26
112.7 GB ([[COLOR=Red]giga[/COLOR]bytes]("http://en.wikipedia.org/wiki/Gigabytes")) = 105 GiB ([[COLOR=Red]gibi[/COLOR]bytes]("http://en.wikipedia.org/wiki/Gibibytes")). That's perhaps where the mixup comes from. Unfortunately, sometimes GiB are referred to as GB, and some people are adamant that one gigabyte should refer to 1024x1024x1024 bytes. Much confusion!

---

### Post by tommcd on 2011-04-27
With 105GB-112GB available for Ubuntu, I would create 3 partitions:
Root 10-15GB This is where the Ubuntu operating system lives.
Swap 1GB This is similar to virtual memory in Windows. If you plan to suspend to memory, make swap at least equal to the amount of memory you have.
Home will be the rest. This is where your data and user specific settings are. 
Here is a great site with tutorials for booting Windows7 and Ubuntu: [http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

And welcome to the Ubuntu forums!

---

### Post by abiss27 on 2011-04-27
**Coffeecat:** Thanks for answering and giving me the two links.

---

### Post by abiss27 on 2011-04-27
**tommcd:** Thanks for the partition scheme and the link on dual booting.

---

