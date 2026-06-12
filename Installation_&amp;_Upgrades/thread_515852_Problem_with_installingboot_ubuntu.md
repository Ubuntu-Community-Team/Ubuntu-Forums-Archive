---
title: "Problem with installing/boot ubuntu"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by olymp on 2007-08-02
hi, i've download ubuntu 7.04 and burn it to CD. When I try to boot from it i see ubuntu logo and after few seconds the system crash and hengup. On screen is shown some kernel error. Only holding the power button works. I rty ubuntu 6.06, kubuntu 7.04 and even ubuntu studio. Exactly the Same problem. I don't know what's wrong. I'v ran memory test and CD test from main menu of ubuntu install CD.
my pc is:
CPU:Pentium 4 prescott 3066 mhz
MB:asus p5gz-mx, chipset i945g/gz
2xDDR2 512mb PC4300
Video: Nvidia 6700 256mb

---

### Post by merlinus on 2007-08-02
Video card problems.  Try the text-based Alternate Install cd.

-merlin

---

### Post by dabl on 2007-08-02
> **olymp said:**
> 

after few seconds the system crash and hengup.



Possibly it only LOOKS crashed due to a failure to auto-recognize your graphics card.  When it does that again, let it sit for a few seconds, then try Alt-F1, and if nothing happens, try Ctrl-Alt-F1.  If you see a text login prompt, we can help.

You might search this forum for that Asus motherboard -- I vaguely recall that others may have had trouble with that model, or possibly the chipset.

---

### Post by olymp on 2007-08-02
what's wrong whith my video card?
i have buildin video. If i remove Nvidia and try to install ubuntu with buildin, will it works? Or i need to buy a new one?

---

### Post by dabl on 2007-08-02
Your video card should work fine, but it will NOT be automatically configured.  Don't worry about that until you've got a running Linux system (text mode). :)

---

### Post by olymp on 2007-08-02
ok, i'll try. 10x a lot

---

### Post by dabl on 2007-08-02
If that i945 chipset includes an integrated graphics system, you'll need to disable that in BIOS, if you want to run the Nvidia 6700. :)

---

