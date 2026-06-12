---
title: "default partition"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by bbmak on 2007-06-21
Hi, i am creating an automation installation for ubuntu (ks.cfg) in my company, and i am having problem with the partition part.

For the swap, i am trying to use recommended, but it seems like this option is not working
part swap --recommended

I am installing into a 20 gig hd.

What is the default partition that i should set??? please help. I am kind of new with the partition.

Here is my partition now
> part /boot --fstype ext3 --size 100 --asprimary
part swap --size 96 --grow
part / --fstype ext3 --size 2048 --grow

---

