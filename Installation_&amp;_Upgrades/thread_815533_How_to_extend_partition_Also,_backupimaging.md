---
title: "How to extend partition? Also, backup/imaging?"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by alexeix on 2008-06-01
Hi,

I'm still a Linux newb, but am loving the OS!!

First problem/question...
I need some advice, because I've installed Hardy Heron over my Vista installation (Wubi), however, I now need to extend my Hardy partition.
I can't find a disk partitioning tool in the menus and from the info I've found on the web, I'm not sure that extending the partition is desirable/possible.
Help!

Second problem/question...
If I decide to put Hardy on a separate disk entirely (which I think I will in the next month or two), is there a simple way to create an image of my Hardy install, so I don't have to go through the hassle of re-installing the OS and all my apps?
I'm looking for an imaging application with a straightforward UI.

Any ideas?

Thanks in advance!

---

### Post by logos34 on 2008-06-01
yep, 

look here:
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by alexeix on 2008-06-03
Thanks for the link, however, I'm not clear if I can use that utility to increase the size of an existing partition.

Can you clarify if that's possible?

Thanks.

---

### Post by logos34 on 2008-06-03
Wubi installs linux INSIDE the windows ntfs parititon.  So you'll have to shrink it first (*use vista's own disk utility, NOT gparted, to do this).  Then create an ext3 parition out of the freed space for hardy transfer.  It should be covered in the lvpm user documentation

---

