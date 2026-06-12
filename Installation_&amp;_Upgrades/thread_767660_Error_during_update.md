---
title: "Error during update"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by shadowkiller137 on 2008-04-25
during the update from 7.10 to 8.04 (AMD64) I keep getting the error 
"Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070419)]/dists/feisty/restricted/binary-amd64/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070419)]/dists/feisty/main/binary-amd64/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs"
during the setting new software channels stage

---

### Post by uranus65 on 2008-04-25
It sounds like you might have to check your repositories in System/Administration/Software Sources.  I would un-check anything but the defaults and let the Upgrade Manager use whatever repository it likes.

---

