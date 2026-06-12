---
title: "video goes crazy on install"
date: 2005-05-12
forum: Installation &amp; Upgrades
---

### Post by gnug on 2005-05-12
I'm having a video problem as soon as I boot off the installation cd and press enter at the initial screen. It goes through the startup but as soon as it seems to enter the actual installation program the screen goes blank and then I get a whole bunch of slanted lines across my screen that jump around rapidly.

I thought the video card (GeForce2 Pro) might be going bad at first so I replaced it with an old TNT2 Ultra but it did the same thing. Then just to make sure I tried installing WinXP on it and that worked fine. I also tried to install Fedora Core 3 on it but it had the 'exact' same problem (same installers I'm guessing?). I also tried Mandriva and its installer actually worked (but I'm not really wanting to use it).

Anyone know what the problem might be?

Thanks

---

### Post by gnug on 2005-05-13
Nevermind, the following got the install working:

linux vga=771 noapic nolapic

(Found it when I pressed F5 for alternate boot options instead of Enter at the beginning).

---

