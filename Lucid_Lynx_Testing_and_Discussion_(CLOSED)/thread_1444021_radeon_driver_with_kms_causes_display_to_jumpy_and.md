---
title: "radeon driver with kms causes display to jumpy and slightly staticy"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by a7phaomega on 2010-03-31
I have just installed Lucid on a macbook pro 2,2 with ati radeon x1600.

From the moment I leave grub and the pretty Plymouth splash screen appears the display starts to hop up and down (kinda like a vcr with tracking problems).

If i turn off kms with the boot flag radeon.modeset=0, then all is fine.

I was just curious if there is some kind of fix that I could try so that I don't just have to turn off kms.

thank you

---

### Post by umberstark on 2010-03-31
You can try "pci=nomsi" (without quotes) at boot instead of any nomodeset option.

Works for my Radeon Xpress 200M.

---

### Post by a7phaomega on 2010-03-31
thanks for the tip. I gave it a shot, unfortunately the problem persists.

---

