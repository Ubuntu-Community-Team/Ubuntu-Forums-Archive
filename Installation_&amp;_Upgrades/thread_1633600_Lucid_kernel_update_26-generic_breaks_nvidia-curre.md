---
title: "Lucid kernel update 26-generic breaks nvidia-current"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by 316479 on 2010-11-29
Xubuntu  10.04 system fully updated
Kernel:  vmlinuz-2.6.32 -26-generic
Nvidia:   nvidia-current-195.36.24

I can't manually compile the nvidia kernel module and hence have no useful video.
In the nvidia-current-195.36.24 directory while running the vmlinuz-2.6.32-26-generic kernel
      make module
      make install
**FAILS**  due to a missing file:   .nv-kernel.o.cmd   for  nv-kernel.o

This worked fine for the vmlinuz-2.6.32-25-generic kernel.

Curiously if I do a package reinstall of nvidia-current-195.36.24 somehow the kernel
module gets built correctly using the automagic of the reinstall process.

---

