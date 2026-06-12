---
title: "ideal partitions for 250gb hdd"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by patilkaustubhv on 2008-11-12
hi, i am planning to install ubuntu 8.10 and virtualize windows in it........

ubuntu would be used for my office jobs while windows for media and gaming......

can any one suggest me ideal partitions for my 250 gb hdd..

thanks

---

### Post by Steve1961 on 2008-11-12
There's lots of ways to do this, including creating a separate home partition.  However, what I'd probably do is create a 50GB ext3 partition for / and a swap partition around twice the size of my ram.  I'd then create a third ext3 partition with the rest of the space and use that for data, the windows virtual machine, and the rest of my docs.

---

### Post by prshah on 2008-11-12
> **patilkaustubhv said:**
> 
can any one suggest me ideal partitions for my 250 gb hdd..


"/" - 12~15 Gb

"swap" - Since you are planning to Virtualise Windows it makes sense to have some extra swap if you have less RAM (< 1.5 Gb):

If you are going to use Hibernate (In host, ie, Ubuntu) feature and :
[indent] RAM <= 512 Mb: 1.5 GB
 RAM > 512 MB : 2 * RAM
 RAM > 1 GB : 1.1 * RAM
[/indent] If you are not going to use Hibernate (In host, ie, Ubuntu) then :
[indent] RAM <= 512 MB: 1.5 GB
 RAM > 512 MB but < 1Gb : 1.5 GB
 RAM > 1 GB but only regular desktop use: 1 GB
 RAM > 1 GB and heavy graphics related work: 2 GB
[/indent]

"/home" - rest of the space.

Make all three primary partitions.

---

