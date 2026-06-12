---
title: "File System Recommendations for 10.4"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by Suicidal State Machine on 2010-06-21
Hi, I'm about to do an install from scratch of Ubuntu 10.4 and was hoping to get some advice on file systems. My plan is to use a solid state drive for the OS and a couple terabyte drives for data (64-bit machine, linux only). 

Should I use ext4 for everything (over, say, ext3)? I found a couple of threads here and elsewhere with mixed reviews but thought I'd ask again now that both the ext4 file system and the Ubuntu 10.4 release are a little more mature. 

Is the performance upgrade significant? Does anyone still see data issues with large files?

---

### Post by Don Barzini on 2010-06-21
I would use **ext4** file system.

It's fine with the latest kernel versions in use.

---

### Post by Tylerjd on 2010-06-22
**EXT4** Is just great, its stable, journaled, and what everyone is switching to. I run it on a netbook, MacBook, and 5 servers no problem.

---

### Post by Suicidal State Machine on 2010-06-22
Thanks for the replies. Looks like the reported cases of lost data due to power outages (caused by delayed allocation) have been patched in version 2.6.30 of the Linux kernel. Most of the reported problems seem to be old threads so I guess I'll try ext4 for both data and OS.

---

