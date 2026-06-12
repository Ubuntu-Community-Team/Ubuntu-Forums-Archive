---
title: "Is there an upgrade to make Ubunutu Wide-screen?"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by ReviewSpin on 2007-01-23
My screen resolution is 1600 x 1200 (I think...)..but Ubuntu can only reach to 1024x768? Whats up with that? Is there an upgrade or something I can do to make it work...because right now Ubuntu looks like stretched crap.

---

### Post by taurus on 2007-01-23
What graphic card do you have and have you installed a driver for it?  Then, modify /etc/X11/xorg.conf to include whatever resolutions you want to use.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by MetalMusicAddict on 2007-01-23
> **ReviewSpin said:**
> My screen resolution is 1600 x 1200 (I think...)..but Ubuntu can only reach to 1024x768? Whats up with that? Is there an upgrade or something I can do to make it work...because right now Ubuntu looks like stretched crap.

Its all about the right drivers and your xorg. ;)

---

### Post by Shatrat on 2007-01-23
1600x1200 isnt widescreen by the way, thats basically double 800x600.
1680x1050 is the nearest resolution to that which is widescreen. 
Most widescreen 20.1 and 22 inch LCDs use this resolution I believe.
You'll need to know for sure which one it is when you configure your xorg.conf

---

