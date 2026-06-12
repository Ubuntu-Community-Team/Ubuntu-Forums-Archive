---
title: "upgrading from CD broke X"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by jnoreiko on 2005-10-13
I upgraded from the CD with synaptic, and rebooted.

X won't run any more.
The error messages sound like it's to do with the nvidia drivers.
How come those weren't updated by the upgrade process?

---

### Post by yesplease on 2005-10-13
My guess is that the Nvidia packages are not in the main repository, because the are not open source.

I think you have to open more repositories in synaptic and search in synaptic for nvidia.  X is probably not broken.

(Others recommended to use synaptic to install the nvidia drivers instead of downloading them from the Nvidia site.)

---

### Post by jnoreiko on 2005-10-13
I managed to get online with the command line, and I followed the instructions in the Hoary Guide for installing the nvidia drivers.

When I try to run x (the command is 'startx', right?) I get the Nvidia logo, then errors again and it won't run.

---

### Post by archivenz on 2005-10-14
how did you upgrade from cd within synaptic?

the 5.10 cd is in my source.list, but it still wants to download about 350mb or so of packages when they should be on the cd

---

