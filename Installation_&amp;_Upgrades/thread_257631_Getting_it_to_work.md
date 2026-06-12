---
title: "Getting it to work?"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by xptweakerntn on 2006-09-14
at first i couldn't get ubuntu to boot from the disk, so i soon realized it was my graphics card. i added a pci geforce and i also have onboard. with my card in, it won't work, but if it's out, it works fine. how can i get it to work? i can't disable the onboard within my bios, i was wondering if i could tell ubuntu somehow to just use the pci card. i really want to use ubuntu, but so far windows has been so much easier. but i still want to make the switch.

---

### Post by hangfire on 2006-09-17
Does your MB have an AGP or PCI-E slot? If so the BIOS may not bother checking for a video card in plain old PCI.

Have you tried the card in different PCI slots? You might also go into LEGACY PnP portion of your BIOS setup, and try to lock in IRQ9 to just the PCI slot that has the Fx5500 in it.

There is probably also some boot line magic that can suggest the PCI card to the kernel, but I don't know what it is.

---

### Post by xptweakerntn on 2006-09-17
no, just three pci slots. as for the legacy stuff, i don't think(or at least know) how or if i can. i will try that though. also, is there a site with "boot line magic" lists?

---

