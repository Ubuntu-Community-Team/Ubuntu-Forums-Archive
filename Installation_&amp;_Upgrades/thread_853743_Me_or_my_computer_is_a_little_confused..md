---
title: "Me or my computer is a little confused."
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by 1fl on 2008-07-08
I want to duel boot kubuntu, gentoo. I have a 40 gig ide and a 120 gig sata.
I did a gentoo install on the 1de, then installed kubuntu on sata.
I want to use the grub from kubuntu I really just need to add gentoo to my existing grub. My confusion is.

Kubuntu labels my drives
sda, ide drive     Kubuntu boots from this drive 
sdb, sata drive    Kubuntu installed on this drive

Gentoo labels my drives
sda sata      (kubuntu)
hdb ide        (gentoo)

I thought bios selected the primary and secondary drives. This is my first time mixing sata and ide drives and just might be normal. I was also hoping to find a good example on google to edit my menu.lst
Seems this shouldn't be to big of a issue. The more I think about it the more I get confused.
Any advice or links would be appreciated, Thanks.

---

### Post by Pumalite on 2008-07-08
I think your problem evolves from the mix of SATA and IDE. Grub gets confused. Tends to think IDE is the Main drive. Search in this forum: 
Dualboot Two Hard Drives 
There are several threads with problems of mix SATA and IDE.

---

