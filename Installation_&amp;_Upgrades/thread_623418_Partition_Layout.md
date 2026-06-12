---
title: "Partition Layout"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by abstractcoder on 2007-11-25
Last time I installed Ubuntu I did a full root install, only a swap partition and main partition existed. I'm working on making multiple partitions. I'm not sure what the size should be of each directory.

Here is my partition drawing (haven't done it yet)

/
/boot
/usr
/var
/tmp
/home


I may add more before I go through with it. Hopefully, someone can help me with the size issue! =)

---

### Post by ag65151 on 2007-11-25
I only have 3 partitions.

/
/home
linux-swap

I don't know why you would want all of those other directories on separate file-systems. /home makes sense because that is where the majority of your settings will be stored. Anyway, the rule-of-thumb as I understand it is

10GB for / (this is really high and you almost certainly won't use it all).
Memory times 2 for swap (I've been told this isn't necessary any more, but I still go by it)
The rest for /home

---

### Post by abstractcoder on 2007-11-25
Any directory tree which a user has write permissions to, such as e.g /home,/tmp and var/tmp/
should be on a separate partition. This reduces the risk of a user DoS by filling up your "/" 
mount point and rendering the system unusable. 

This is not strictly true, since there is always some space reserved for root which a normal
user cannot fill. It also prevents hardlink attacks.


Any partition which can fluctuate, e.g. /var(especially var/log) should be on a separate partition.

From a security point of view, it makes sense to try to move static data to its own partition, and then mount
that partition read-only.

etc.... all of this is found in a pdf called "securing debian"

---

### Post by dmcnulty on 2007-11-26
I have nearly the same layout as ag6561, but with a smaller / partition.  I'm actually a long-time Mandriva user, and just started using Xubunta yesterday on an old low-end machine because it was advertised as a good distro for near-antiquities.  Mandriva first-time installs make the /, swap, /home layouts by default.  The big advantage of this setup is that even if you do a fresh install (as opposed to an upgrade), the /home partition is never touched, so you don't lose your settings.  I've even put Web files under /home so that they stay intact after replacing Apache.  I don't know if Ubuntu fresh installs work this way, but I'm hoping I can administer my MDV and UBU with the same procedures.

-  Dennis  :)

---

### Post by ag65151 on 2007-11-26
I hadn't thought of partitioning for security. That is interesting. Thanks for the info. Given that I am thinking of repartitioning to assign /var /tmp and others their own partitions. I will probably just divide up the space I have already allocated to / 

I really like having a huge /home It makes my life easier when upgrading.

Thanks again for the info.

---

