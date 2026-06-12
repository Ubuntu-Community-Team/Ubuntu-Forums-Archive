---
title: "Ubuntu 7.04 on a laptop Dell Inspiron 1300"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by iulian on 2007-06-09
Hi,

I have a problem in installing Ubuntu 7.04 on my laptop Dell Inspiron 1300.

I can boot the live cd, run the install and when I get to the partitioning stage I choose manually to have a dual boot system, Windows and Ubuntu, but I can't create ext3 and swap partitions. I can create only one partition: ext3 or swap. And I have sufficient space: 20 gb where 19 gb for ext3 and 1 gb for swap partition.

You have any idea? I couldn't find anything related to this problem on web.

Thanks!

---

### Post by confused57 on 2007-06-10
> **iulian said:**
> Hi,

I have a problem in installing Ubuntu 7.04 on my laptop Dell Inspiron 1300.

I can boot the live cd, run the install and when I get to the partitioning stage I choose manually to have a dual boot system, Windows and Ubuntu, but I can't create ext3 and swap partitions. I can create only one partition: ext3 or swap. And I have sufficient space: 20 gb where 19 gb for ext3 and 1 gb for swap partition.

You have any idea? I couldn't find anything related to this problem on web.

Thanks!
You can have only 4 primary partitions on a hard disk, one of which can be an extended partition, which can contain many logical partitions...have you tried making the ext3 & swap logical partitions?

Here's an  excellent guide for partitioning:
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

