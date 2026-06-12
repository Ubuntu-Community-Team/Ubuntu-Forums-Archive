---
title: "trouble upgrading upgrading linux-image-2.6.12-10-686"
date: 2006-05-04
forum: Installation &amp; Upgrades
---

### Post by riverfr0zen on 2006-05-04
Tried to run the latest updates on my Breezy laptop with Synaptic - everything seems ok, except for one package - upgrading linux-image-2.6.12-10-686 (version 2.6.12-10.30)  to version 2.6.12-10.32.

I get the following error:

E: /var/cache/apt/archives/linux-image-2.6.12-10-686_2.6.12-10.32_i386.deb: unable to create `./lib/modules/2.6.12-10-686/kernel/drivers/ide/pci/aec62xx.ko'

The file in question seems to already exist on my system -

-rw-r--r--  1 root root 19016 Mar 11 12:43 /lib/modules/2.6.12-10-686/kernel/drivers/ide/pci/aec62xx.ko

Any ideas what the problem could be?

---

