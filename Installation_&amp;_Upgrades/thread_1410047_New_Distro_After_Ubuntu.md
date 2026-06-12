---
title: "New Distro After Ubuntu"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2010-02-18
If I install let's say Mandriva after Ubuntu, can I Then just delete the Partitions That It Made to get rid of it or will this affect Ubuntu or else how can I get rid of it if I don't want it?

---

### Post by darkod on 2010-02-18
As long as you don't install mandriva's grub, and you keep using your ubuntu grub on the MBR, you could delete the partition without any problem. When installing second, third linux distro I would usually keep the grub from the first, in other wods, when installing mandriva look around for Advanced options and tell it not to install grub.

Then from ubuntu if using the new grub2 just run:

sudo update-grub

and it will add mandriva to your menu.

---

