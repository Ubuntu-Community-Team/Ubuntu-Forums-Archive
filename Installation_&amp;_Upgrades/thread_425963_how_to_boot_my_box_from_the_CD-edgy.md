---
title: "how to boot my box from the CD-edgy"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by Franscisco on 2007-04-28
Does anyone know what are the things to follow in order to boot my dapper version box from the Edgy cd. What I want is to install edgy, but my box can't detect the cd when booting. Any help would be nice!

---

### Post by Schalken on 2007-04-28
Use the update manager to upgrade, or put the CD in while in Dapper (see the wiki for info).

To actually boot from the Edgy CD, you need to configure your BIOS to look for a boot CD. Hit Del (or whatever else it says) as your computer starts to enter the BIOS setup screen, then look for "Boot devices", "Boot order" something similar (I can't remember where it is exactly off the top of my head). You move your CDROM to higher in the list than your hard drive. Save and exit setup and your computer should reboot into the Edgy CD.

---

