---
title: "swap logical or primary?"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by redarmy on 2007-06-30
Hallo all,:popcorn:
I'm trying to install ubuntu 6.06 next to my existing win2k. Before I ran this alternate CD, a partition had been made free/unpartitioned by means of Partitionmagic 7.0 in win2k. When I came to partition section, and first defined part of it as primary ext3 at /, but the rest of undefined part was automatically designated as primary. According to some posts, swap partition should be logical. In addition, I'd like to define a /home partition as logic. How could I get around this issue?  

Nr. 1 primary 7.3gb b k ntfs /media/hda1
Nr. 5 logical 10.5gb    k fat32 /media/hda5
         primary 10.2gb    ext3 /
         primary     2gb freier speicher                        ????

thanks in advance

---

### Post by redarmy on 2007-06-30
has nobody come across such situation? :(

---

### Post by confused57 on 2007-06-30
Here's an excellent guide on partitioning:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
or
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

It doesn't really matter if swap is logical or primary...it's just that there's a max of 4 primary partitions to a hard drive...partitioning definitely has to be pre-planned, it's noted in the first link that you cannot create a primary partition between 2 logical partitions(which are contained within a primary extended partition).
You can open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
-l is a small "L"
this will show your partitions

---

