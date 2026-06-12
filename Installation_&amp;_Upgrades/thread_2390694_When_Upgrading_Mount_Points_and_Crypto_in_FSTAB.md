---
title: "When Upgrading? Mount Points and Crypto in FSTAB"
date: 2018-05-01
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2018-05-01
On installing 16.04 onto an SSD I put Cryptography. Those bytes were dd'd from a metal to a solid state drive. What came over with that clone was the crypto partition. I no longer use/want encryption.

I would like to use APTIK ( [http://www.teejeetech.in/p/aptik.html](http://www.teejeetech.in/p/aptik.html) ) a tool designed to migrate apps from one release to another. APTIK backs up mount points. I don't want it to restore any encryption work/schemes. But if it does, how can I delete the mount points and partitions, should it reproduce them?

I would like to migrate all user installed apps, their associated dependencies, the user installed configuration files and all data, without fuss. APTIK will do this, but I have to know what damage might happen so as to ask questions after the migration, if necessary.

---

### Post by rsteinmetz70112 on 2018-05-01
I'd probably try to use rsync to copy the entire system to new partitions then modify the fstab as necessary.

---

