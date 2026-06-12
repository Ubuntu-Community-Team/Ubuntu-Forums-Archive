---
title: "debian installation help"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by kdelover_123 on 2011-03-18
Hi guys,

This Question is related to a debian installation (sorry for posting in ubuntu forums).

I'm trying a network installation by dumping the contents of debian 6.0 DVD onto my http server and booting the installation candidate using a minimal CD.

The error i get after selecting the debian mirror to download installer components is ```
'dists/squeeze/Release is unsigned'
```.What do i have to do to make is signed?

I tried skipping this verification procedure by adding the boot parameter ```
'debian-installer/allow_unauthenticated boolean true'
```,but verification still seems to be happening.

---

### Post by Dutch70 on 2011-03-18
Welcome to UF, but you can probably get more help here.

[[COLOR="Red"]http://forums.debian.net/[/COLOR]]("http://forums.debian.net/")

---

### Post by kdelover_123 on 2011-03-18
I passed the boot parameter allow_unauthenticated=true,which worked.

The new problem is the Western Digital IDE HDD doesnt get detected when i click on 'detect disk',same problem when i switch to a Seagate SATA HDD !!

---

