---
title: "no display during hardy install"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by olivine on 2008-05-01
I get a "cannot display this video mode - optimum resolution 1280x1024 60Hz" right after pressing "install" using Hardy (alternate 64bit). I tried changing some of the options (F6) without success. Is there any option I can add to the boot command that shows up after initially hitting F6, so I can install Hardy in a video safemode?

The same happens when I try installing Gutsy. This is on a computer that has Edgy (!) running fine.

---

### Post by olivine on 2008-05-01
Before starting install, press F6, and add "vga=795" (or "vga=775") to end of boot command line, to force 1280x1024 during install.

Problem solved. :)

Later on, Hardy crashes during software install step (at ~6%, maybe during xserver install?), but that may be a different issue. Install works for Gutsy.

---

