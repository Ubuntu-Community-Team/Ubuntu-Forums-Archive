---
title: "Worthless display in 10.04"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by davidoz on 2010-07-30
I'm trying to install Ubuntu 10.04 on an old (2007) UMPC. Desktop, Alternate and Netbook have all been tried. The hardware has previously run 9.10 Desktop.

My first problem is the display. It's a mess. Even a text terminal (Alt+Ctrl+F1) doesn't work - all I get is a few pixels smeared across the screen. The installer's bootup text and splash screen display OK, but after that the display is worthless.

I've tried vga=771, pci=noapci, noapic, nolapic and nomodeset, without success. That's all I could glean from the help. I freely admit to having little idea of what I'm doing.

Clearly, something changed radically between 9.10 and 10.04 and it's orphaned my hardware. Is there a way around it or should I just give up on Ubuntu?

Hardware details:-
Processor: x86 Family 6 Model 13 Stepping 0 CentaurHauls ~1197 Mhz	
BIOS: American Megatrends Inc. AB150F05, 7/05/2007
Video:
- Controller: VIA/S3G UniChrome Pro II IGP
- LCD Resolution: 800 x 480	
- Bits/Pixel: 32

The chipset is not unusual, so there's probably a simple answer. Unfortunately, my best efforts have failed to find it.

---

### Post by Robert A. Morin on 2010-08-03
Hmm, curious.  I ran the BootCD and after the Ubuntu splash, the screen went completely blank, the monitor just went into power safe mode, and couldn't wake up, regardless of which key I pressed, or mouse button or movement I made.  Here's my setup, wonder if this may be significant.

Gigabyte GA-MA790GPT-UD3H 790GX Motherboard
Corsair HX620W PSU
AMD Phenom II x955
8GB DDR3-1600 (4x2GB)
128GB SSD + 500GB HDD + 640GB HDD
LG 8x Blu-ray Burner
Sapphire ATI HD5850
Dell UltraSharp 2408WFP
Logitech G15 Keyboard, MX518 Mouse
Z-2300 2.1 Speakers

---

