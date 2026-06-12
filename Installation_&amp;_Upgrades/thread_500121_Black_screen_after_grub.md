---
title: "Black screen after grub"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by _tigg_ on 2007-07-13
Ok so i've just installed Ubuntu onto a partition (Vista is on the other) But when I select ubuntu on the Grub it just goes to a black screen. I had the same problem when trying to start the live session, even in safe graphics mode. I managed to get around that by changing the display from VGA to 1024x768x32 which worked fine, yet I can't find a equivalent there.

Installing 7.04 (amd64)

Hardware
*Mobo* Asus P5B delux Wi/Fi
*Graphics card* Nvidia 8800GTS
*CPU* Core 2 Duo E6600

I'd really appreciate any help, I haven't been able to find anything elsewhere.

---

### Post by rillip on 2007-07-13
Try adding 
```
vga=791
``` to the grub menu.  You can edit the menu by pressing "e" with the selection highlighted.  The above goes right after the bit that should look like "ro quiet splash" at the end.

---

