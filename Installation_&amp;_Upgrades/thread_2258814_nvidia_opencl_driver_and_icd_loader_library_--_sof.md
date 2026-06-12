---
title: "nvidia opencl driver and icd loader library -- software updater will not work"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-12-30
Recently, each occurrence of Software Updater shows a security update for nvidia opencl driver and icd loader library.  However, the tick boxes are empty and one cannot tick them.  So the security update does not load.  Hardware is DELL Vostro 3500 with nVidia graphics.  OS is 14.04 64-bit.  Current video driver is 331.113.  Do i have a security issue?

John

---

### Post by grahammechanical on 2014-12-30
Ubuntu 14.04 is a stable release. Therefore, any update comes under the Stable Release Update (SRU) policy. And then there is Phased Updates, which is what you are seeing. Those updates are held back for you but other users have received them and if those users do not report any problems then those updates will be allowed to be installed on your system. Updates to proprietary video drivers can and do cause problems. You can read all about it.

[http://lwn.net/Articles/563966/](http://lwn.net/Articles/563966/)

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

> [COLOR=#000000][FONT=Times New Roman]Ubuntu quietly introduced a new mechanism in its 13.04 release that progressively rolls out package updates, pushing each update to a small subset of the total user base first, then steadily scaling up, rather than publishing the update for everyone simultaneously. "Phased updates" (as they are known) are designed to catch and revert buggy package updates before they are propagated out to the entire user community.[/FONT][/COLOR]

[http://www.murraytwins.com/blog/?p=127](http://www.murraytwins.com/blog/?p=127)

Regards.

---

