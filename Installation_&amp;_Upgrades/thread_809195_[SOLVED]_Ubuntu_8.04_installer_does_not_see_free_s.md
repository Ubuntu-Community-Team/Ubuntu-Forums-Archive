---
title: "[SOLVED] Ubuntu 8.04 installer does not see free space"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by darexx on 2008-05-27
I am trying to install UBUNTU 8.04 in a dual boot configuration.

I have 180 GB unallocated free space on the drive and a 46 GB windows partition and I would like to install Ubuntu to the free space.

However the Ubuntu guided install is not giving the option to install into the free space but only into the existing windows partition.

I could install Ubuntu using the manual option. However I would much prefer to let Ubuntu determine where to put swap and mount partitions as I have no idea about best practice on these issues.

Could anyone help as to how to get the guided install to pick up the free space?

---

### Post by darexx on 2008-05-27
Ok I have a possible answer to my question above.

It is mentioned in the link (good article by the way):
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
that with the text install there is an option in the partitioning tool to get UBUNTU to automatically partition the free space for you.

I will try this later and see how I get on

---

### Post by darexx on 2008-05-28
AAHHH!!!

For other Ubuntu Newbies - in order to do a text install you have to download a different ISO - The "alternate CD".

Anyway I downloaded this and it did indeed give me the option to automatically partition the free space - so that was good. I now have the partitioning set up by Ubuntu. Nothing very exciting as it turned out. Just one partition for root and something like 6GB for swap which seems a lot.

I am not sure if it put the swap at the end of the disk. I remember reading somewhere that swap should be in the middle of the disk for best performance but maybe that is outdated now.

Tip: if you download the DVD install this includes the alternate CD and gives the option to install using text straight away. It also includes more software so this is what I will be doing in the future!

---

