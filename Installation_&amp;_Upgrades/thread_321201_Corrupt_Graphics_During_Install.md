---
title: "Corrupt Graphics During Install"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by PsypherPunk on 2006-12-18
I'm trying to install Kubuntu 6.10. However, during the install, just after the word 'Kubuntu' and the logo disappear from the screen, the screen is filled with bright, vertical blocks.

I've seen something similar to this before (using an Nvidia 6600GT and Samsung SyncMaster 550s monitor) and usually got around it by passing 'vga=normal' as a parameter. However, it doesn't seem to be working in this instance.

Any ideas?

---

### Post by PsypherPunk on 2006-12-19
Okay, fixed by starting a second session, editing xorg.conf to use the 'vesa' drivers and not 'nv', then restarting X.

---

