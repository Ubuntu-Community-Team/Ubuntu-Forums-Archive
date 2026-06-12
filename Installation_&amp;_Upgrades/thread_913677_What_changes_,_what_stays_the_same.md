---
title: "What changes , what stays the same ?"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by Hagar55 on 2008-09-08
Right now I'm using Hardy, but as always I'm curious for the next release.
If I upgrade to Ibex I'll get a different kernel to choose from when I startup. Do I get the full stable install if I choose the hardy Kernel after upgrading or is it just the kernel and do all the things I try changing in the Ibex kernel affect the Hardy one as well....

I hope the question is understandable....

---

### Post by Sef on 2008-09-08
> **What changes , what stays the same ?**             
All the packages pretty much will be upgraded.  The kernel will be newer.  I think it will be 2.6.27.  It will be the default, but if you have problems with it, it would be possible to use an older kernel on your system.

---

### Post by manishtech on 2008-09-08
When you get a kernel update it is showed up on the GRUB listing so that in case your new kernel update doesnt work, you can continue with the older configuration.

---

### Post by Hagar55 on 2008-09-09
Will chanes in fstab and other configuration parameteres change for all the kernels or just the one you're working in ?

---

### Post by manishtech on 2008-09-09
> **Hagar55 said:**
> Will chanes in fstab and other configuration parameteres change for all the kernels or just the one you're working in ?
fstab is a file which specifics the mounting of partitions when the system is booted. In short it contains mounting information of volumes.

---

