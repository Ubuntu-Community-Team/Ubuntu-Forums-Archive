---
title: "Ubuntu will not install on Compaq Presario laptop"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by eaglesfan17 on 2007-11-28
When I am trying to install Gutsy on my laptop (any flavor - Ubuntu, Kubuntu, or Xubuntu) the same thing happens every time. With the live cd, I get passed the initial splash screen, but the desktop environment refuses to load - I get a blank screen and nothing happens.

I have tried alternate installs on all of the CDs as well, but to no avail. As soon as the Xserver starts to install, the screen goes completely black and nothing ever happens.

Here are my laptop specs:

Compaq Presario F700
AMD 64 X2 Dual Core Processor 1.80Ghz
1.5GB RAM
nVidia geForce Go 6100
Currently has Vista installed

Has anyone else experienced a similar problem? Also, I have tried both x64 and x32 versions of Ubuntu.

I would think that my laptop is fully capable of running Gutsy, but maybe I'm just wrong.

---

### Post by x64Jimbo on 2007-11-28
You tried the alternate install CD isos? Like the blue and red screens to set everything up? If you did this, try waiting for a little bit after the screen goes blank. It will most likely come up.

---

### Post by eaglesfan17 on 2007-11-28
Yeah, I did try the alternate CDs and the screen never came back.

I did some digging and found that the live CDs will boot with the "noapic" option. Is there any reprocussions or anything that I need to know before installing with that option?

---

### Post by juanchorossi on 2007-11-28
Im having the exact problem on a HP notebook. I tried "naopi", "nolapi" commands but nothing happens: Splash screen disappear when loading and theres no way back, either with Ctrl + Alt + Bckspace
Thanks in advance

---

### Post by Disz on 2007-12-01
Use the 64 bit gutsy livecd.

When the initial boot screen loads, hit F6 and append the following to the end of the boot arguments there;

<space> noacpi<space>pnpbios=off

That should allow you to start the livecd environment. 

-D.

EDIT: I ended-up with the following boot options in my menu.lst: noapic nolapic pnpbios=off acpi_irq_balance.

---

