---
title: "NV7922u with second 640 gig hard drive partition error"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by DWade on 2011-05-05
hope this right place to post.

I got a new hard drive was having a partition error  on windows 7 partition on 500 gig drive

got new 640 gig 7200 rpm drive installed using same as 500 gig, but changed sda3 win7 from 100 gig to 136 gig, extended partition 485 gig, 400 gig ntfs data partition, rest 2 partition, Ubuntu, and swap.

Ubuntu would not see data partition.  It must be smaller than 400 gig.  is there a read limitation on extended partitions?

---

### Post by DWade on 2012-04-15
I put this up back in May of 2011 when I bought a new 640 gig hard drive.

I forgot about this.

But in several post about portable hard drives it seems to be having the same problem 

here's one for example [ubuntuforums.org/showthread.php?t=1953523]("ubuntuforums.org/showthread.php?t=1953523")

So if the partition is greater than 400 gigs, it not being recognized.  Is the a Kernel problem?

---

### Post by DWade on 2012-04-20
An update to the problem.  Reduce the second partition [a secondary partiton of 640 gigs] to under 400 gigs, with rest unallocated withing the secondary partition, but Ubuntu, still would not read the secondary partition.

Reduced the total size of secondary partition to under 400 gigs the unallocated outside of the partition and it would read it.  Changed it to a primary partition and increased its size up to full 640 and Ubuntu would read it.  

What is wrong with the Ubuntu kernel not being able to read a secondary partition over 400 gigs in size?

---

### Post by DWade on 2013-04-29
This is still sitting here unanswered.
So I will re-ask like this;
this is my harddrive 640 gig setup
sda1 = 60 gig -- win 7
sda2 = 60 gig -- testing 13.04
sda3 = 80 gig -- 12.04 LTS
extended partition sda4
sda5 = 435 gig -- ntfs data
sda6 = 5 gig swap file

sda5 un readable in 12.04, 11.10, 11.04, 10.04.  sda5 is in an extended partition and is larger than 400 gigs and is un readable. Is this a problem with Linux?

To make the partition readable had to change the extended partitions as follows;
sda5 - 240 gig -- ntfs data
sda6 - 5 gig -- swap file
sda7 - 195 gig - ntfs

I have a 640 gig usb drive. I had to change the secondary partition of 540 gig to a primary partition, now it's readable in Ubuntu
It was this
sdc1 100 gig -- software backup ntfs
sdc4 secondary partition 540 gig
sdc5 540gig -- backup ntfs

had to change to this to read
sdc1 -  100 gig primary
sdc2 - 540 gig primary
now the over 400 gig is readable in linux

Can some please till why a secondary partition of over 400 gigs is not readable?

---

