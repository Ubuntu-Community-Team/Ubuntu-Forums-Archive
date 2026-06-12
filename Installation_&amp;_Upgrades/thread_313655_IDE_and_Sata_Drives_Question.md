---
title: "IDE and Sata Drives Question"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by Guns90 on 2006-12-06
Good day, ya'll.  If I use an IDE drive as my hda1 and a SATA drive as my hdb1, how do I set the jumpers - both as master or slave on the SATA drive?

---

### Post by bulldog on 2006-12-06
As far as I know the Sata has no jumpers,or it must be to swith between sata1 and sata2.
Sata disks are sda not hda.

Your IDE drive must be master and your Sata is master by default.
You can change the master boot device in your BIOS though.

---

