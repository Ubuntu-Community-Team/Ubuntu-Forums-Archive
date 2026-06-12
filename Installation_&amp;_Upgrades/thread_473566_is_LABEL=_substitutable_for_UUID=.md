---
title: "is LABEL= substitutable for UUID="
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Stephen Howard on 2007-06-14
Hi, given the recent problems with hd / sd  following the change from the Sata to Pata driver, I'm beginning to see the inevitability of having to move away from directly referencing my harddrives (eg /dev/sda).

The problem is that UUID is butt ugly, unreadable to humans and fails whenever I format / resize / encrypt a partition (ie swap). 

LABEL is much more readable, so I was wondering if adopting that would be a long term solution?  Or will I discover when I next upgrade that the Ubuntu installer, init scripts and/or grub will only deal with UUID?

---

### Post by mcduck on 2007-06-14
Yes, you can use label as well.

---

