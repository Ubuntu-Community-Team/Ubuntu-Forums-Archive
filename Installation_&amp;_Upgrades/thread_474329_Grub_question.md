---
title: "Grub question"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by SOG420 on 2007-06-15
Ideally I would like to install Ubuntu, openSUSE,  and Fedora Core 7 on the same machine in a multiboot learning environment. I am able to install both openSUSE and Ubuntu but whenever I install a Second OS the grub entry from the previous OS disappears. Thanks

---

### Post by 67GTA on 2007-06-15
Each OS will rewrite grub to use it's bootloader. Usually you have to edit /boot/grub/menu.lst and manually add the other OS's. Take a look at the link for some examples.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

