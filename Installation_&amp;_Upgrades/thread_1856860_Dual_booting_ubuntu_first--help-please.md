---
title: "Dual booting ubuntu first--help-please"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-10-09
I have ubuntu 11.10 installed all works fine, now I need to install windows 7, I need an up to date guide of how to do this.
a nice link will be very welcomed.

---

### Post by Elfy on 2011-10-09
Backup prior to editing partitions.
Boot the livecd/usb - run the partition editor - shrink the existing - get some unallocated space at the beginning by moving partition if necessary.
Boot with the windows install disc, install it.
Check it works.
Boot with the livecd again and reinstall grub.

---

