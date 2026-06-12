---
title: "[SOLVED] Tried to Use Gutsy instead"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by charlesbw on 2008-07-14
Since Hardy Heron was not detecting my hard drives, i tried using gutsy instead, but right after i choose to install or lauch the live CD (after the first options) the screen goes dark and my monitor looses its interaction with my video card (I know because it says "No Input" and my monitor only does that when its unplugged from my computer). The video card is a XFX 8800 GT Geforce,uses DVI cables.  I was trying to install Gutsy then upgrade to Hardy...any suggestions to solving the video card problem with Gutsy?

---

### Post by overdrank on 2008-07-14
> **charlesbw said:**
> Since Hardy Heron was not detecting my hard drives, i tried using gutsy instead, but right after i choose to install or lauch the live CD (after the first options) the screen goes dark and my monitor looses its interaction with my video card (I know because it says "No Input" and my monitor only does that when its unplugged from my computer). The video card is a XFX 8800 GT Geforce,uses DVI cables.  I was trying to install Gutsy then upgrade to Hardy...any suggestions to solving the video card problem with Gutsy?

HI and have you tried using the safe graphics mode from the initial boot of the live cd? You may also try and edit the kernel and add vga=771. Press F6 and the remove the quiet splash and add the vga=771 or 775.

---

### Post by charlesbw on 2008-07-15
thanks i will try the F6 option, i already tried the safe graphics mode and got the same result.

---

### Post by charlesbw on 2008-07-15
thank you overdrank, your vga=775 suggestion did the trick. lets see if hardy allows me to upgrade.

---

### Post by overdrank on 2008-07-15
> **charlesbw said:**
> thank you overdrank, your vga=775 suggestion did the trick. lets see if hardy allows me to upgrade.

Good luck! :)

---

