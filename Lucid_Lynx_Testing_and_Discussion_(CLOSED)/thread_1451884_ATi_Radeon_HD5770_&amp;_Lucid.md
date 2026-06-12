---
title: "ATi Radeon HD5770 &amp; Lucid"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by meklu on 2010-04-11
**IF YOU RUN INTO THE SAME PROBLEM, PLEASE TRY RUNNING THIS IN THE TERMINAL:**
```
sudo aticonfig --initial -f
```reboot:
```
sudo reboot
```and you should be done.
__________________________

I can't seem to get my HD5770 to work with Lucid (64-bit) and I always have to boot in low graphics mode. In karmic it nearly worked (threw the not-so-funny unsupported hardware watermark.) Jockey doesn't help at all and 3d sure isn't working (can't get e.g. glxgears running). I will post more info if requested.

---

### Post by Volcom3 on 2010-04-11
Is ur ATI on board or a PCI card?

---

### Post by overdrank on 2010-04-11
Moved to Lucid Lynx Testing and Discussion :)

---

### Post by meklu on 2010-04-11
As I have a desktop PC, it's a PCI-E card.

---

### Post by BrokeMahPC on 2010-04-11
If you have installed the proprietary driver with system - administration - hardware drivers upon reboot you do get that "do you wish to boot into low graphics?" screen.

You need to type this in a terminal:
sudo aticonfig --initial -f

It will configure the driver and the xorg.conf. Reboot again and you should be fine.
(you also need to do this if installing a downloaded driver from the AMD website)

---

### Post by Volcom3 on 2010-04-11
I ran into alot of issues with my ATI graphics card. So I ran out and picked up this one and changed it out. Galaxy NVIDIA GT 220 1GB DDR2 PCI Express Graphics Card. Everything ran perfect after that.

---

### Post by meklu on 2010-04-11
Thank you very much BrokeMahPC! I had already tried running "aticonfig --initial" (without the -f operand) as a normal user and root as well.

---

### Post by lvleph on 2010-04-11
> **meklu said:**
> Thank you very much BrokeMahPC! I had already tried running "aticonfig --initial" (without the -t operand) as a normal user and root as well.

Um that was an f, not a t.

---

### Post by meklu on 2010-04-11
> **lvleph said:**
> Um that was an f, not a t.
Um that was a typo.

---

