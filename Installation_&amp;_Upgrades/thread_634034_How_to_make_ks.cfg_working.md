---
title: "How to make ks.cfg working?"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by corsa on 2007-12-07
I tried to make a gibbon auto-installation CD.

What I did was..

1.put ks.cfg made by kickstart in the root of ISO
2.replace isolinux.cfg in /isolinux and made some changes:

append ks=cdrom:/ks.cfg file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

but it doesn't work.nothing happened but entered the live desktop the same.

Where's the wrong?

---

