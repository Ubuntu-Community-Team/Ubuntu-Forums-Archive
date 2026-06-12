---
title: "After  8.04 update, Grub shows old 2.6.22 Kernel"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Czar on 2008-04-19
Today I updated from 7.10 to 8.04 and it appears when running update-grub that the latest kernel installed is 2.6.24-16... Yet on boot the only choice I have is the oldest 2.6.22-14...

What gives?

---

### Post by logos34 on 2008-04-19
Post your /boot/grub/menu.lst

Maybe you have line 113 set to #howmany=1.  Or the other kernels are listed but commented out.

---

