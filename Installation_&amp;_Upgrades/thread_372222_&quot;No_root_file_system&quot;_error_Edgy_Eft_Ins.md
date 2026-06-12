---
title: "&quot;No root file system&quot; error Edgy Eft Install"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by yerokleoh on 2007-02-27
Ok, so, when I try to install Edgy Eft on my usb hard drive from the install on the live CD desktop, I go into manually edit partition tables, because i've already put a 12 gig ubuntu ext3 partition on it and a 2 gig swap partition. I set up root to mount at /sda5(my ext3 partition) and swap on my 2 gig swap partition. It then says no root file system when I click next. I honestly know nothing about Linux, so any help would be MUCH appreciated. I'm not computer dumb, just Linux dumb. :(

EDIT: Both my ext3 and swap partitions are logical.

---

### Post by mikewhatever on 2007-02-28
The root partition must be mounted as simply /. 
/sda5 implies there is already a root partition, and you are mounting another one as /sda5.

---

