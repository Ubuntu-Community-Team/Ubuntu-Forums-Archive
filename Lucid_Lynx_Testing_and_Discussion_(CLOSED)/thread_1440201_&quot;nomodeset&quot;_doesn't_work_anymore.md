---
title: "&quot;nomodeset&quot; doesn't work anymore?"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-03-27
"Nomodeset" doesn't have any effect any more. Had to revert to "radeon.modeset=0"... I need to go in UMS due to, still not solved, random crashes in KMS... Also there is a considerable regression in screen refreshment while scrolling as of this morning... In UMS I do not see any regression... (ATI HD3650, xorg-edgers) Is it only here or...?

---

### Post by timosha on 2010-03-27
When I use "nomodeset" in kernels 2.6.32-16 and -17 booting just stops after plymouth appears. Only a power off/power on cycle helps.

---

### Post by umberstark on 2010-03-27
> **zika said:**
> "Nomodeset" doesn't have any effect any more. Had to revert to "radeon.modeset=0"... I need to go in UMS due to, still not solved, random crashes in KMS... Also there is a considerable rgression in screen refreshment while scrolling as of this morning... In UMS I do not see any regression... (ATI HD3650, xorg-edgers) Is it only here or...?
Try using "pci=nomsi" instead of any nomodeset option at boot. KMS works fine for me now (Xpress 200M) although 3D performance isn't that great.

---

### Post by zika on 2010-03-27
> **umberstark said:**
> Try using "pci=nomsi" instead of any nomodeset option at boot. KMS works fine for me now (Xpress 200M) although 3D performance isn't that great.I'll try it in a couple of minutes. Thanks... "Message Signal(ed) Interrupts"... I'll investigate a bit...

---

### Post by zika on 2010-03-29
"Nomodeset" not working was my mistake: namely, there was radeon-kms.conf left in /etc/modprobe.d that wask keeping radeon.modeset on 1. Since I have some problems with 2D rendering (covered in separate thread) I, still, need to work mostly in UMS. I did not have opportunity to see if KMS, still, generates random crashes. I did not encounter any, while beeing in KMS, but I'm, now chasing what is the cause of 2D rendering regression... It seems it is somehow connected to Rhythmbox since it ceased between two RB upgrades... Testing...

---

