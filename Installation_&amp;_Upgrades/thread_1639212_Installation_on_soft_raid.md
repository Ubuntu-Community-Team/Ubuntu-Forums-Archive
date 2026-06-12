---
title: "Installation on soft raid"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by dmwyatt on 2010-12-06
I'm trying to come up with a plan for my home server and just wanted to discuss my options.

I have three 1.5TB hard drives that, at first blush, I would put into a RAID 5 array created by mdadm.  In fact, I just did this with a 10.10 live cd to do some testing.

In my ideal world, I would install Ubuntu to this array.  However, I would like to take the majority of the space of these three drives and pool them with other RAID 5 arrays I have in the system via LVM2.  I don't know how well this would work.  

Basically my questions boil down to this:

Can Ubuntu be installed on a mdadm-created RAID 5 array?

Would I be better off making smaller partitions on the three 1.5TB drives, make a RAID 5 array out of those partitions, installing Ubuntu on that array, and then making a RAID 5 array out of the remaining space on those drives so that I can then add that to my LVM volume group?

Any thoughts about how you would structure this?

---

### Post by IndyGunFreak on 2010-12-06
I'm not sure what you plan to use your server for... but you saying "Home Server" makes me think a home file server.

Have you considered FreeNas?  It may not meet your needs, but it sure made my life much less difficult.  The beauty of it is, other than the hard drives, I was into it for about $95.

IGF

---

### Post by dmwyatt on 2010-12-06
It's mostly a file server, but I also will be using it for development and other things, so I really would like to use Ubuntu.

---

### Post by SaturnusDJ on 2010-12-11
Yes, Ubuntu can be installed on RAID5. RAID arrays and LVMs are also possible to create during the setup.

I think your idea of creating larger partitions later is a good idea.

---

