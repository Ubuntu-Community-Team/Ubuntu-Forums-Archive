---
title: "Flickering after upgrade to Maverick (radeon rv710, hd4350)"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by todd534 on 2011-02-12
Post title says most of it. I'm using tv-out, but it worked fine in Lucid. 

Attaching xorg.conf, xorg log, and results of get-edid. I figure it may be a faulty refresh rate thing, but I don't know how to fix such a thing. I did try adding an additional refresh rate with 

$ gtf 800 600 30
$ xrandr --newmode "800x600_30.00"  17.01  800 792 864 928  600 601 604 611  -HSync +Vsync
$ xrandr --addmode DIN 800x600_30.00

but that didn't help.

---

