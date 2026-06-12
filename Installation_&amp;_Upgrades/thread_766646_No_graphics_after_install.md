---
title: "No graphics after install"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by oddworld on 2008-04-25
I just installed ubuntu 8.04 using the alternate i386 cd. The desktop cd was not working too well.
After checking for errors, the alternate installation went perfectly, but upon rebooting there are no graphics.
I saw the ubuntu splash screen loading bar, and I heard the drums, but the screen is really screwed up.
Ctrl Atl F2 yields a really fuzzy / blocky screen and I cant make out any text.
When I booted the desktop CD, I noticed it worked somewhat well using "safe graphics".
I have an Nvidia 6800GT AGP.
Any ideas?

---

### Post by oddworld on 2008-04-25
I booted into recovery mode and typed:
```
sudo dpkg-reconfigure xserver-xorg
```
but that did nothing.
I still have no graphics at all after the ubuntu splash / drums.
Any ideas?

---

### Post by oddworld on 2008-04-25
I reinstalled using desktop CD and live CD install.
This seemed to work, now I have graphics.
I don't think this should be marked solved though, I never fixed the old problem.

---

### Post by chek2fire on 2008-04-25
What video card you have? And give to terminal 
glxinfo 
and post it here without the zeros in the end :P

---

