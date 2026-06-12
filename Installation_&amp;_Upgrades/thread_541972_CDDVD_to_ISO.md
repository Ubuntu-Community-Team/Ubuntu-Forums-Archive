---
title: "CD/DVD to ISO"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by NEMESIS0744 on 2007-09-03
Are there any programs that allow you to create ISO files from CD/DVD? If so, how do you install it?

---

### Post by logos34 on 2007-09-04
> **NEMESIS0744 said:**
> Are there any programs that allow you to create ISO files from CD/DVD? If so, how do you install it?

Make an ISO from CD/DVD:

Load media but don't mount it. If it automatically mounts,  unmount it.

> [B]dd if=/dev/cdrom of=cd.iso 
dd if=/dev/dvd of=dvd.iso[/B]

---

### Post by ubuntukerala1980 on 2007-09-04
mkisofs

---

### Post by vanadium on 2007-09-04
There is no need to unmount the medium before using dd. The question of the original poster is on creating an iso image from a dvd or a cd. mkisofs works in the other direction: it allows to create a cd/dvd/ image from files for burning on a cd/dvd/

---

### Post by ubuntukerala1980 on 2007-09-04
thx for finding my mistake :lolflag:

---

### Post by logos34 on 2007-09-04
> **vanadium said:**
> There is no need to unmount the medium before using dd.

Yes, but it's a good idea.  All the instructions I've seen recommend it.  (i.e. to prevent random access during copying).

---

