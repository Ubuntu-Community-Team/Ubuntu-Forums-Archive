---
title: "no init found. error. unknown filesystem"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by gpost3 on 2011-06-09
hi mates,

i have my ubuntu running in software raid 0 configuration. when grub loads, i get 

> error: no such device: xxxxxxxx
error: unknown filesystem

then grub loads fine and during ubuntu load up, i see the ubuntu icon but immediately get the following error:

> no init found

and i get to initramrd prompt. how to fix this issue?

---

### Post by gpost3 on 2011-06-10
issue fixed. ran fsck and repair the filesystem.

---

