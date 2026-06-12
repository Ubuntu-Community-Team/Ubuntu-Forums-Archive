---
title: "After updgrade, 20.04 goes to blank screen after GRUB"
date: 2020-09-30
forum: Installation &amp; Upgrades
---

### Post by Hibari on 2020-09-30
So, I upgraded from 18.04 to 20.04 and apparently something went wrong, but I can't figure out what it was.

I need to press ESC to bring the GRUB menu out, but after that it seems to load normally, gives out a bunch of OK lines about how it successfully started this and that, then it goes blank and the display shows a NO SIGNAL warning.

Booting in recovery mode works fine, though.

Any ideas?

---

### Post by ajgreeny on 2020-09-30
How did you do the upgrade, using a GUI system or command line?

What hardware do you have, particularly the graphics card?
Using recovery mode please run command ```
inxi -G
``` and tell us what it says.

---

### Post by Hibari on 2020-09-30
Upgrade was done the boring way via GUI.
I have installed the new AMD drivers via their website and it actually loads now (if I bring up GRUB manually), but it's a jumbled mess graphically, absolutely unreadable.

Here's the output:

> Device-1: AMD Cedar [Radeon HD 5000/6000/7350/8350 Series] driver: N/A   Display: x11 server: X.Org 1.20.8 driver: vesa unloaded: fbdev,modesetting 
  resolution: 1152x864~N/A 
  OpenGL: renderer: llvmpipe (LLVM 10.0.0 128 bits) v: 3.3 Mesa 20.0.5 




---

### Post by deadflowr on 2020-09-30
> **Hibari said:**
> Upgrade was done the boring way via GUI.
I have installed the new AMD drivers via their website and it actually loads now (if I bring up GRUB manually), but it's a jumbled mess graphically, absolutely unreadable.

Here's the output:

There are no drivers for that card on their website.
Any drivers from amd for that card are unusable on newer versions of Ubuntu.
The open source drivers provided by Ubuntu are the only ones you should use.

Basically installing any drivers from the amd website has broken the gpu, thus why it shows as using llvmpipe.
You'll need to remove them.

---

