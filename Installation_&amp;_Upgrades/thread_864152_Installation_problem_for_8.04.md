---
title: "Installation problem for 8.04?"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by v0ice on 2008-07-19
Hi!

I've been trying to install Ubuntu 8.04 from the LIVE CD (x86 and x64) on a empty HDD (clean partition).

After I boot the computer and choose to install Ubuntu it says Loading Linux kernel 100%, then the Ubuntu loading screen with the loading bar appears.
**The problem is that after about 12 seconds the progress bar stops, the cd-rom stops spinning and the computer freezes**.

This is happening to all the versions, even in safe graphics mode.

I have tried the Alternate CD, but the same thing happens when **I get to the Ubuntu progress bar screen, it freezes after 12 seconds**..

I've checked all the CD's for defects, no problem.

I've also tried to remove the "quiet splash" from the boot text by pressing F6.

And I've tried with about every other boot option avaliable?
Including:

highres=off
nohz=off
irqpoll
noapic
nolapic
pci=routeirq
pci=noacpi
acpi=off

[B]The installation always seem to stop at this line:
[ 134.360226] PLX9052 PCI/PCMCIA adapter: mem=0xefdff000, plx_io=0xbf00, irq=16, pccard_io=0xbe00[/B]

Thou, sometimes the starting numbers differs and the IRQ number differs.

My guess as a first time Ubuntu user, is that it has something to do with the graphics?
Ubuntu is not supporting dual graphic cards or what?

Any help is greatly appreciated as of now I don't really have any operating system at all.

My Hardware:
Striker Formula II
Intel Core 2 Extreme X9650
GeForce 8800GTX OC SLI


Best Regards
André

---

### Post by v0ice on 2008-07-19
Solved the problem. Had to take out the netgear wireless network adaptercard. Now it works like a charm :)

---

### Post by hansdown on 2008-07-19
Hi vOice. Glad you got it going and welcome to the forums.

---

