---
title: "Can't boot from a USB stick? Got  &quot;boot error&quot;?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by kooldino on 2011-10-14
Try running this command on the USB stick first:

#sudo mkdosfs -v -I /dev/sdb

This apparently puts your USB stick in superfloppy mode.

NOTE: the above command assumes that your USB stick is sdb.  If not, change accordingly.

---

