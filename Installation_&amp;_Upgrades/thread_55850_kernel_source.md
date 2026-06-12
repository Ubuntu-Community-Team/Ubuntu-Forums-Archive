---
title: "kernel source?"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by Radi0ShacK on 2005-08-10
Hi all,
i was just wondering where i can get kernel source of the default kernel that comes with Hoary ? as i want to install my smartlink/sl-modem driver. Thanks alot in advance :)

---

### Post by areguly on 2005-08-10
[QUOTE=Radi0ShacK]Hi all,
i was just wondering where i can get kernel source of the default kernel that comes with Hoary ? as i want to install my smartlink/sl-modem driver. Thanks alot in advance :)[/QUOTE]
 
apt-get install kernel-package linux-source-2.6.10

or apt-get install kernel-package linux-source-2.6.11 if you want 2.6.11 from Universe.

---

### Post by az on 2005-08-10
You do not need to recompile your kernel.  Just use the kernel headers and forget about the source.

Use the linux-headers package.  linux-headers-2.6.10-5-386 is on your cd.  Install build-essential, too.

---

