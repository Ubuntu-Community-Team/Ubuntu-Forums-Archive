---
title: "update-initramfs disables encrypted partitions."
date: 2008-06-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by storm99999 on 2008-06-05
I'm quite surprised by Intrepid being so stable early on because I had bad experiences with late beta and release candidates of prior versions.  However, whenever an update forces an update-initramfs, the new initramfs doesn't contain the scripting to decrypt my full drive encryption and I have to revert to my older initramfs (which is now backed up and GRUB points to, but I still test newer ones).

Anyone else having this problem?  I'm trying to isolate what exactly is missing before I report it.

---

### Post by RAOF on 2008-06-05
I'm pretty sure what's missing is the lsb-helper scripts; the cryptsetup stuff is still there, they just don't work because they try to include some files not in the initrd.  Please file that bug, if there isn't one already :).

---

