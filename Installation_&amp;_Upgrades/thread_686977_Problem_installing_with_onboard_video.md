---
title: "Problem installing with onboard video"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by Taristar on 2008-02-03
Ok trying to help a friend install xubuntu 7.10 on a Asus P4BP-MX it has an Intel 845GV chipset with onboard video.

Don't see any jumpers on the motherboard or anyway to disable the on board video in bios.

We got xubuntu installed using text mode with the on board video set at its max 8mb.

We have a Chintech Geforce 5200 256mb card we would like to use that is PCI.

Just not sure how to tell linux to disable to on board and look at the PCI for primary video.

Any help would be appreciated.

Otherwise we need to track down a good deal on a 478 socket motherboard with an AGP slot and no on board video or where the on board can be disabled. Have a 6600 GT AGP card he can use if we could switch out the motherboard.

---

### Post by manimal347 on 2008-02-03
You can't tell Linux to disable your onboard video; you were right to assume that this is a function of your motherboard. Some motherboards indeed cannot have the onboard video disabled, though this is rare. Try checking your user manual. If you've lost it, the motherboard's manual is almost certainly available online in PDF format. Most likely, the video chipset is disabled in BIOS. Try poking through it and see if you can't find an option pertaining to your graphics solution. The startup splash-screen/messages on your computer should tell you what key to hit to enter the BIOS setup; it varies from company and era, though ctrl-alt-del, esc, and del have always been pretty common.

Unless you need to run OpenGL games, though, or own a gargantuan monitor, even the stock video is probably overkill and will have a fine 2D accelerator core for xwindows use.

Your manual:
dlsvr02.asus.com/pub/ASUS/mb/sock478/P4bp-mx/e1534_p4bp-mx.pdf

---

### Post by Taristar on 2008-02-04
Yeah tried poking thru bios and downloading manual only lets me change between 1 or 8mb of video memory tried updating the bios and everything and nothing.

---

