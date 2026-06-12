---
title: "Switching from Fedora 8"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by Pro$pect on 2008-07-24
Right now I am running vista and fedora 8 on my hp dv6500 laptop. I would like to delete fedora and install ubuntu but, my computer uses grub as the boot loader so if I delete my linux partition I will run into problems booting into windows right? Just looking for the right way to do things.

---

### Post by kellemes on 2008-07-24
> **Pro$pect said:**
> Right now I am running vista and fedora 8 on my hp dv6500 laptop. I would like to delete fedora and install ubuntu but, my computer uses grub as the boot loader so if I delete my linux partition I will run into problems booting into windows right? Just looking for the right way to do things.

If the partition scheme you currently use for Fedora is fine for you, you can simply pop in the Ubuntu disk and install it into the same partitions. It will overwrite Fedora and (re)install Grub (and include a Windows entry in the bootmenu).. and all will be fine.

---

### Post by Pro$pect on 2008-07-24
well then, guess its a lot more simple than I thought!

---

### Post by Pro$pect on 2008-07-24
It never asked what partition to install to and ended up wiping out everything...good times. Guess all I can do is get ndiswrapper working on this some how so I can still use it since I don't have the vista cd.

---

