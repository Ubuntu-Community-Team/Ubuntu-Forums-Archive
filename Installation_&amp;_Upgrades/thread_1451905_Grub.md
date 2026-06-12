---
title: "Grub"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by WeyOh on 2010-04-11
Hi,

I'm sure this question is explained somewhere, but I'm not too sure what to look for.

Basically I had a Ubuntu installed on one partition, and then I installed another linux distro on another partition. Now, when I boot my computer the grub menu.lst file that appears is the one of my latest install.

How can I make the menu.lst file of my initial ubuntu installation be the one that appears?

Thanks!

---

### Post by tom4everitt on 2010-04-11
Boot into your old system, and run the command:

sudo grub-install /dev/sda

---

