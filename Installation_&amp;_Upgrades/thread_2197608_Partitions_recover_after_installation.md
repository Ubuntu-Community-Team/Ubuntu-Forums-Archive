---
title: "Partitions recover after installation"
date: 2014-01-04
forum: Installation &amp; Upgrades
---

### Post by tootmis on 2014-01-04
I just tried to install ubuntu server. Have choisen my USB drive  to install but somehow installation have deleted all my partiotions with  ubuntu and so on.

  My previous installation with ubuntu was in the center of HDD and I  think it is still possible to recover files. The first part of disk was  just for some temporarly info , Games and not so important information  and I think this could not be recovered because of new installation.

  I need help because ACRONIS don't work  and I don't know any other methods of recovering partition and files...

  PLS HELP ME!

---

### Post by xangor on 2014-01-04
try testdisk program: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by thommy3 on 2014-01-05
> **tootmis said:**
> I just tried to install ubuntu server. Have choisen my USB drive  to install but somehow installation have deleted all my partiotions with  ubuntu and so on.

  My previous installation with ubuntu was in the center of HDD and I  think it is still possible to recover files. The first part of disk was  just for some temporarly info , Games and not so important information  and I think this could not be recovered because of new installation.

  I need help because ACRONIS don't work  and I don't know any other methods of recovering partition and files...

  PLS HELP ME!


This sounds like a grub boot section problem. If my guess is correct, your partitions are still there and all that has been changed is the boot flag.

Before you installed ubuntu server, your HDD was flagged as boot, but after instaling the new System, there is a conflict with grub on the usb stick. Grub might have been changed to use the usb stick, so it might be that all you have to do is install grub on the hdd again.

Did you check with a live system disk whether your partitions are still there?

(the other possibility is, that by installing ubuntu server you accidentally deleted all other partitions.)

---

