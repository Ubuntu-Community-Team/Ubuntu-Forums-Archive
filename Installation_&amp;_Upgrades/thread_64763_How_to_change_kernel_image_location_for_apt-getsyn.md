---
title: "How to change kernel image location for apt-get/synaptic"
date: 2005-09-12
forum: Installation &amp; Upgrades
---

### Post by Whatsisname on 2005-09-12
Greetings

Awhile back I purchased a new harddrive and moved my linux installation. I was able to move all the partitions and the kernel image and whatnot, and set everything up in the grub menu.lst fine. However, every time synaptec trys to update my system it changes the menu.lst to be back to the old configuration. Does anyone know where the info is stored for dpkg-reconfigure so that I can change it so that this annoying reconfiguration problem doesnt happen again?

Thanks.

---

### Post by tonym on 2005-09-12
Have a look at your menu.lst file.  Towards the top are a number of lines that look like comments (ie start # ) but are in fact default configurations for things like root partition and grub root.  These are used whenever update-grub is called to automatically create the menu.lst file,  including when installing a new kernel.

Correct these and you should be OK.

---

