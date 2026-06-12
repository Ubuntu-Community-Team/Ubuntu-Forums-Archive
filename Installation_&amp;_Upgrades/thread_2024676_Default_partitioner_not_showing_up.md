---
title: "Default partitioner not showing up?"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by bradpurvis on 2012-07-14
I'm using a live environment, and i'm trying to install ubuntu. The easy partitioner isn't showing up and i'm getting this[http://i.imgur.com/zbgwi.jpg]("http://i.imgur.com/zbgwi.jpg") I'm really not experienced with installing in this method.

---

### Post by darkod on 2012-07-14
It looks like windows is not recognized, so the option to install along it is not shown.

In any case, you will need to shrink the 1TB ntfs partition because it takes the whole disk. You unallocated space for ubuntu. You should do this in windows Disk Management. Restart windows few times after that in case it wants to do some checks.
Also check if the disk is not Dynamic in Disk Management. It should be Basic.

After that is done, start the install process again and see if you have different options.

---

