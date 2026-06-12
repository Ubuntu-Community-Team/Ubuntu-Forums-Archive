---
title: "Double-Partitioning Question"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by Valkyr333 on 2011-03-05
Hey all,

So my computers are both double-partitioned between Windows XP Professional and Linux Kubuntu 10.04. I'm preparing to eventually ditch Windows and use Kubuntu exclusively with both computers, they're both laptops. I've heard that when double-partitioning, it's possible to either install one partition inside another, or install them independently of one another. However, if one is inside the other, deleting the first OS in which the second is installed will result in deleting both of them and effectively rendering the computer useless. I don't know which of those two happened when I double-partitioned, so my question is, how do I figure it out?

Thanks,

-Val

---

### Post by mikewhatever on 2011-03-05
Run **df -h** and look and the output. If Ubuntu is on a /dev/loop device then it's installed into a file within another file system, or, in other words, not on a separate partition. Entries like /dev/sda1, /dev/sda2, etc, on the other hand, designate partitions.

---

### Post by Valkyr333 on 2011-03-07
```
valkyr@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   11G  5.2G  67% /
none                  2.0G  344K  2.0G   1% /dev
none                  2.0G  100K  2.0G   1% /dev/shm
none                  2.0G  200K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda2             221G   77G  145G  35% /host
```

^Result of df -h. I'm guessing this means I'm not separately partitioned. When I get to the point where I'm ready to reinstall Ubuntu as a separate partition, what are the correct steps to make this happen?

Thanks for your  help. =)

-Val

---

### Post by Sean Moran on 2011-03-07
> **Valkyr333 said:**
> When I get to the point where I'm ready to reinstall Ubuntu as a separate partition, what are the correct steps to make this happen?
-Val
#1: Make sure you know beforehand which partitions on your hard disk are okay to use.  You can resize partitions during the install, but it's slow.  Best to have all your important Windows CODE and DATA defragmented and resized to smallised partitions to begin.

When you do the installation, and get to the part about hard disk partitions, select MANUAL (Advanced), and take a look at the layout of your hard disk.

If you have 10GB of unallocated space, use that.  Hopefully you know the difference between primary and logical partitions, because you'll only get four primaries to set carefully, and if one of those is set to EXTENDED, then you can make many LOGICAL partitions inside that one big EXTENDED partition.

Ubuntu can install on either primary or logical partitions.

First, make sure there is at least 10GB of free unallocated space, and then set the SWAP partition as 2GB of that space.  Then set your root (/) partition to 8GB, and if you have some more space, you can allocate the rest for /home/.

It's complicated, but you only have to do it right once.  Then it's easy from there.

---

### Post by oldfred on 2011-03-07
Just to add a few things to Sean Moran's post.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Partitioning.

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

