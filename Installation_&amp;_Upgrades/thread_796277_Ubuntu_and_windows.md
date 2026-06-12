---
title: "Ubuntu and windows"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by ferod on 2008-05-16
I have hardy installed perfectly works wonders. Although i can sufficiently play games on wine I think for the moment I'd rather have a small windows partition for counterstrike and WoW. Is it wise to install windows after Ubuntu or should i wipe the drive and install windows then Ubuntu afterwards?

---

### Post by hermes0710 on 2008-05-16
You can install windows and you will just have to reinstall grub after its installation. The partition of windows doesn't exist right? You should use gparted to shrink the one that hosts ubuntu instead of any other windows application

---

### Post by tribaal on 2008-05-16
Windows shouldn't kill your Ubuntu partition (it will install itself in whatever partition you specify).
However it will overwrite your bootloader (Grub), with it's own, which will make Ubuntu unaccessible.
You can however restore your MBR from a liveCD afterwards, which should do the trick.

- Trib'

---

### Post by ferod on 2008-05-16
Awesome, ty guys, vry much.

---

