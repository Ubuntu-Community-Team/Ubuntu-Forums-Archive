---
title: "Stuck in INIT 3 after Live CD Load"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by Alkaif on 2006-10-21
Hi there,

I've been trying out many different flavours of the linux operating systems and so far i've had no luck with the hardware configuration that i've got. Either at times compiz would not load/work on SuSE Linux 10.1 (I don't know, I've always asked questions in the forums but nothing seems to fix it) and I don't have my sata drives showing up (Asus A8V-MX motherboard) so here i am trying out Ubuntu 6.06LTS.

I put the cd in, boot the cd and there is no display, instead i'm stuck on terminal login prompt. What should I do? Is there a way to install ubuntu without loading the desktop? I've got an Nvidia 7600GS AGP gfx card so maybe thats why its not loading up the drivers for it to make the display work.

Is there any way to fix this? please?

Cheerio,
Alkaif.

---

### Post by mgmiller on 2006-10-21
From your INIT 3 screen, try editing xorg.conf
```
sudo nano /etc/X11/xorg.conf
```

I think in the liveCD, if it asks for a password, you can leave it blank and just hit enter to continue.

Scroll down to the section "Device" that shows your nvidia card in the "Identifier" line and in the next line called "driver" change the entry from "nv" to "vesa".  

Save the file and then from your command line type, 
```
startx
```

You should be on an unaccelerated graphical desktop.
If you choose to install Ubuntu, you can then experiment with installing easyubuntu (lookup with google) and try installing the accelerated drivers for nvidia.  I don't think easyubuntu works in live CD mode.

Good luck.

---

