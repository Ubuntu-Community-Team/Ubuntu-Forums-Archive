---
title: "Can't get graphical display on LTS Live CD"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by EntropicTundra on 2007-02-10
I can't get X to give me anything on 6.06 LTS AMD64 Live CD. Everything works fine in text mode, until it tries to switch to graphical output, and my monitor goes on standby. (Switching to a login screen with Ctrl-Alt-F1 works fine.) I've tried safe graphics mode, forcing the resolution, changing the driver in xorg.conf (to "radeon" *and* "vesa"), and changing the gfx card output (switching the cable). But nothing will give me anything.

Specs: Abit AN8 Ultra (chipset = nForce4 Ultra), Athlon64 3500+, Radeon X800XT VIVO (has DVI output only), 1GB DDR RAM, Maxtor 120GB Serial ATA HD, Western Digital 250GB Serial ATA II HD

EDIT: Looking through /var/log/Xorg.0.log, I noticed the cause seems to be the monitor values - complaints about the hsync and vsync rates, and the interlace/doublescan settings which I can't find anywhere in xorg.conf. I've tried changing the sync rates according to the monitor's spec, but still no luck. (I think it's to do with the card itself, as the monitor complains about "no signal" rather than "I can't display this".) It also thinks I'm using a CRT monitor (monitor is an LG L1780Q - 17" LCD).

Any thoughts? Suggestions?

---

### Post by EntropicTundra on 2007-02-25
*bumpage*

---

