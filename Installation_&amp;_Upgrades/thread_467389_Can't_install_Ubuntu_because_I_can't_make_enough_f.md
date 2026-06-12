---
title: "Can't install Ubuntu because I can't make enough free contiguos space  :("
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by benton on 2007-06-07
Hi there,

I want to install Feisty as dual-boot on a 60GB HD with 55% free space. So far I've de-fragmented the HD with three utilities (XP built-in de-fragmenter, Diskeeper, DIRMS) and every time I try to install Feisty it complains that there's not enough free contiguous space.

Is there anything else I can do? Right now I can't afford to use the whole disk for this install so I'm trying the dual-boot option.

Thanks in advance for any hints,

-Benton

---

### Post by merlinus on 2007-06-07
Use gparted live cd to shrink your windows partition.  But make sure there is not a hidden restore partition on your machine.  This is often installed by the dells of the world.

gparted is available from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Good luck!

-merlin

---

### Post by hessiess on 2007-06-07
crate the partitons manualy. it ses that there isant enugh free space becose the free space is part of a partition. you wll haft to shrink that partition to make some free space:)

---

### Post by benton on 2007-06-07
> **hessiess said:**
> crate the partitons manualy. it ses that there isant enugh free space becose the free space is part of a partition. you wll haft to shrink that partition to make some free space:)

Thanks for the tip, I'll sure try it. However the first time I installed Ubuntu as dual-boot on a different PC (one HD with only one Windows partition), I did it the exact same way I'm trying now and I didn't have to defragment the HD at all, not even once. I didn't resize the partition either and the installer finished the job perfectly. Go figure.

Thanks,

-Benton

---

### Post by merlinus on 2007-06-07
You do not HAVE to defrag, but it is preferred because it will free up more space.

Also, I prefer manual partitioning, so I can see beforehand exactly what is going to happen.

In other words, I ain't about to have to re-install windows and apps yet again!!!

Unfortunately, I need it for only one app which I cannot do without for my business.

-merlin

---

