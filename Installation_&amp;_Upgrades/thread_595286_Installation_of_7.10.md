---
title: "Installation of 7.10"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by patrickalexson on 2007-10-28
**Alright, talking about 7.10.** Sorry if someone else has the same problem, I would post in that area or look at that thread.

**Ok, ive been using 7.04 with no problems**, except that I was unable to use Macromedia Flash, which sucked - but I can go without flash (AND YES) I have tried the alternatives and they were very glitchy.

**So, I proceeded to download the x86 version of Ubuntu 7.10.** I ran the live cd, no problems, and proceeded to install. Dont ask why I didnt just upgrade, Im not sure why I didnt either :)

**Install went through fine, showed up in my dual boot menu.** SO I try to access it for the first time. I hit enter to boot to Ubuntu from the dual boot screen. The screen flickers, starts to load, flickers again, like its going to chnage to the Ubuntu splash screen, and then othing happens. It just stays black. Im thinking mabey a driver issue? Graphics card? BUT, then again, 7.04 ran and installed without problems so why would a newer version glitch?

Here are my specs:

Acer Aspire 3050 Laptop
AMD Sempron 3500+
1.5 Gigs of DDR2- 533mhz
ATI Radeon Xpress 1100
Dual Boot **Windows XP SP2** and **Ubuntu Linux x86 v7.10 **(Previously 7.04)

---

### Post by zvacet on 2007-10-28
From grub menu select recovery mode and boot to it.

```
dpkg-reconfigure xserver-xorg
```

Select **vesa** and if you get graphic search the forums for installaton of ATI drivers.

---

### Post by patrickalexson on 2007-11-05
Right ok, worked, but isnt it supposed to save it...or at least I would expect it to save the configuration so that I can boot into Linux normally.

Cause it will allow me in AFTER I reconfigure settings, but it never saves it. Noob alert! How to save configuration so that I dont have to go and redo everything?

Also, anyone know how the heck to get Macromedia flash to work with Firefox on those specs? Do not give me alternatives unless they are glitch free cause I have tried a few of the 3rd party ones and I have installed them correctly but I have yet to get one that works correctly.

---

