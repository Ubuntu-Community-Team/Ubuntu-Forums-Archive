---
title: "Dual Boot Laptop HELP!!"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by cbennett926 on 2011-03-08
Ok, so, I will be buying a laptop in the coming months for college and my intention is to run Ubuntu as my primary operating system, but I still want to have Windows 7 as a crutch. I know there are multiple ways to do this (Wubi, seperate hard drives etc.) but I was wondering if it were possible to just install it and if there were an option to partition your existing hard drive so they are virtually seperate from each other.

---

### Post by zenwalker on 2011-03-08
You dont have to go for wubi or seperate installation. Use virtualbox or vmware and virtualize the OS of your choice.

---

### Post by cbennett926 on 2011-03-08
True, but I want to have a 100% full install, but still have a dual boot, so my question is on the install if there is an option to partiton both windows and Ubuntu?

---

### Post by Quackers on 2011-03-08
Yes.
First make sure that only 3 or fewer primary partitions are in use on the hard drive. If you already have 4 primary partitions STOP! You will need to delete one.
If you have no unallocated space on the drive you should use Windows disk management console to shrink the size of the C: partition (after defragging the system!).
Then in the Ubuntu installer you can partition that free space for Ubuntu installation by selecting the manual option in the partitioning stage.

---

### Post by Rubi1200 on 2011-03-08
For a really excellent guide to dual-booting, see here:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by cbennett926 on 2011-03-08
Thank you guys so much!! I want to be more involved with Ubunut, but I can't find any general chat forums on here, but that is unrelated so I will call this one solved.

---

