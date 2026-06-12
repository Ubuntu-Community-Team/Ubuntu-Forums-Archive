---
title: "dual boot 9.04 with 9.04 64bit"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by DarinB on 2010-01-28
1. can i dual boot 9.04 32 bit with 9.04 64 bit?
2. use the same ./home (mine the 9.04 32bit is on a separate hdd) 
3. or just make it separate partition on the sda the os partition? 
FYI i already dual boot with win vista
4. or can i dual, triple, quadruple boot with any other ubuntu distros or linux distros, ie puppy linux just to play with it.

---

### Post by zvacet on 2010-01-29
1. yes
2. I´m not sure (someone else will know better)
3.related to previous question but yes you can make separate home
4. yes you can multiboot 

P.S. Why install same version of ubuntu ( I know it is 32 an 64 bit difference but still...).Take one with you like more (I´m not sure how far 64 get so I think 32 may be your choice).

---

### Post by DarinB on 2010-01-29
any idea how to do it?

also can i dual boot with puppy linux or maybe debian etc just to spread my wings a bit experiment but not commit yet

---

### Post by Ravernomina on 2010-01-29
> **DarinB said:**
> any idea how to do it?

also can i dual boot with puppy linux or maybe debian etc just to spread my wings a bit experiment but not commit yet

Back Up Clear your hard disk

Make 20 Gb for each OS you want on your Disk, 
They all have GRUB so they can add each other
Make a 2 GB swap partition (all the OSes can use the same SWAP partition)
Make the rest of the space a /home Partition
On every install tell it to use /home partition for your home folder (if it says to format, just ignore it)
Install and Enjoy

---

### Post by DarinB on 2010-01-29
does each os get a different partition for the os. and can i do that during the os installation or do i have to partition before hand?

---

### Post by Ravernomina on 2010-01-29
> **DarinB said:**
> does each os get a different partition for the os. and can i do that during the os installation or do i have to partition before hand?

Yes Each OS gets its own Partition.. it has 2

And yes u can do this during an OS installation

---

### Post by oldfred on 2010-01-30
It is better to plan your partitions in advance. Some have said /home should not be shared among distributions as applications may be different versions and not necessarily work correctly.  I created a separate /data partition and link all the standard folders in /home to the data partition. My /home only has 1GB of mostly hidden folders & files with 3 years of config data and all my data files photos, movies, firefox & thunderbird profiles are in the data partition.

[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

### Post by zvacet on 2010-01-30
@ DarinB

If you want to multiboot just linux OS then you can format entire HD as extended partition and inside of it make logical partitions.That way you will avoid 4 primary partitions limitation.

---

### Post by DarinB on 2010-01-30
Arigato gozaimasu Ravernomina san

---

