---
title: "Lost virtual file system"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by richard0707 on 2012-07-09
Hi,
I ran a WUBI upgrade from 11.10 to 12.04 recently and have had a meltdown.

Booting fails around about Grub.

Looking at the hard drive from either a Ubuntu Live CD or from Windows the root.disk file is 0 bytes.

Is there a recovery strategy for the virtual file system?
the Swap file appeared to have 256M in size.

---

### Post by YannBuntu on 2012-07-10
Wubi is ok to try Ubuntu, but it's safer to install it OUTSIDE Windows (= [standard installer]("https://help.ubuntu.com/community/GraphicalInstall")) for a long-term use.

If your root.disk file is 0 bytes, and if you have no home.disk , everything is lost.

---

