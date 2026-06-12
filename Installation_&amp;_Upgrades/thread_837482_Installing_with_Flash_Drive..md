---
title: "Installing with Flash Drive."
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by Kyle_vdk on 2008-06-22
I want to mount the iso to a flash drive.. how would I get by.. doing this..

---

### Post by Pumalite on 2008-06-22
1. Make flash drive bootable with syslinux
2. Download the vmlinuz and intrid.gz from the ubuntu archives (not the cd ones - this is why people can't mount the flash drive as CD)
3. get the isolinux.cfg from the cd and rename it syslinux.cfg
4. get a copy of an iso you want to install. dont extract or rename the iso.
5. drag those files into a flash drive
6. boot from it and the install shall go normally without needing to mount anything

any details can be found from the internet or this forum. search install edgy from iso (its the same guide done with edgy)

---

