---
title: "Karmic installer cannot see my SATA drives."
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by themusicalduck on 2009-10-27
After upgrading from 9.04, I decided I might as well do a fresh install to see if things will run a bit better.

I formatted my / drive in gparted to ext4, but the installer can only see my one IDE drive. Both of my sata drives aren't listed.

Using the noacpi option and the nodmraid (or something like that) appeared to show up one of my sata drives, but not it's partitions and it still didn't show the drive I actually want to install onto. Also I want to install it manually, since there is a particular partition I want to use.

Strangely, on normal bootup with no additional options, the live CD can see all my drives and partitions as I'd expect. Its just the installer that cannot see them. I can even format partitions in gparted with no problem.

---

### Post by themusicalduck on 2009-10-28
bump

---

### Post by xebian on 2009-10-28
try removing all your drives but the one you want to install into.

---

### Post by themusicalduck on 2009-10-28
Didn't help :(

---

