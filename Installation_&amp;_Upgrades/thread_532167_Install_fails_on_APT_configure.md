---
title: "Install fails on APT configure"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by shawn6913 on 2007-08-22
Good Morning Ubuntu gurus,
I have "flattened" my windows box and in the process of installing Unbuntu on it. I first removed all partitions and booted with the newest install CD. I then checked the CD for integrity which it passed with no errors. I selected use the whole disk for the install.
The install went fine until it got to the 82% mark where it was configuring apt. I just hangs there. The disk is 60Gb so there should be plenty of space.

Does anybody have any idea about what may be the problem?

---

### Post by undertakingyou on 2007-08-29
I had this same problem.  I found that if I unplugged the network cable all was good; it overcame that hurdle.  I then did have to tell the install to skip trying to download the package lists.  Hope it helps.

---

