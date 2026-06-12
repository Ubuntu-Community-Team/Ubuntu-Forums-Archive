---
title: "roblem updating fresh 7.10 install."
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by solidsteel144 on 2008-02-23
I get the following error message:

E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2

Any ideas what's going on?

---

### Post by solidsteel144 on 2008-02-23
I found the issue. The update file was corrupt so I logged in to root and deleted and re downloaded the file. It finally installed correctly! :)

---

