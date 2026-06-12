---
title: "Problem when install in vmware"
date: 2005-04-06
forum: Installation &amp; Upgrades
---

### Post by Sapab on 2005-04-06
HI

When i am installing ubuntu in vmware on a win xp machine i will have a notice about the installation cannot find my harddrive when it is going to start the partionmanager.

I can installinig other linux dists but not ubuntu.

How should i do??

---

### Post by liverpoolfc on 2005-04-07
When you create the virtual drive, try using an IDE drive instead of the default SCSI.  I've seen this problem with some other distributions, and I fixed it by telling VMWare to make the virtual drive IDE.

---

