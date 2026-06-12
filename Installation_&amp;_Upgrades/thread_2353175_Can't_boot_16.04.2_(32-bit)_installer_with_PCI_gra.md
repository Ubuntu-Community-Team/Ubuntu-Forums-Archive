---
title: "Can't boot 16.04.2 (32-bit) installer with PCI graphic card"
date: 2017-02-19
forum: Installation &amp; Upgrades
---

### Post by bronxio on 2017-02-19
Hi! I've been surfing on the Internet trying to fix this, but can't find it out.

I've a Dell Optiplex GX520 with dual boot (Windows and Ubuntu Studio), which hasn't expansion slot for graphic card (the PCI-e 16x slot is not included on this model). I've already installed Ubuntu Studio 14 LTS on it with integrated graphic card and worked fine, but I bought a second hand PCI nVidia GeForce FX5200 (to be able to have two monitors), and problems appeared: Windows nor Ubuntu Studio couldn't boot! They crashed and reboot everytime while the booting process. I guess that it's "too hardcore" for OS to change from PCI-e bus to PCI for graphics (because I also guess the integrated graphic card is on the PCI-e bus).

So, after reinstalling Windows, everything ok for it. But trying to boot Ubuntu Studio live, it crashes and reboot. I tried introducing in Grub the "nomodeset" command, but now it shows diagonal white lines and stop.

I suppose that I need to boot in some special way to be able to boot and install. Maybe with privative drivers will work... but first it must boot. I've tried Ubuntu 10 LTS, and it works (so I guess that I just need to do something manually first). But 12 not. So, maybe after the 10 version, Ubuntu developers changed something assuming that very few would try to install Ubuntu with a PCI GPU... I don't know.

Any suggestions for next step trying to fix this?

Cheers!

---

### Post by wildmanne39 on 2017-02-19
*Thread moved to **Installation & Upgrades**.*

---

### Post by efflandt on 2017-02-20
I didn't even know they made an FX5200 in PCI, the one I had (long ago) was AGP (are you sure your card is PCI?).

It is interesting looking back at a brochure for the FX series compared with today's graphics cards:```
ROCKET SCIENCE FOR A SYSTEM-LEVEL SOLUTION
• 0.13&#956; process technology for higher levels
of integration and higher operating clock
speeds**
• Copper vias and wiring**
• Advanced thermal monitoring and thermal
management**
• 256-bit memory interface*
• Support for up to 256MB
• AGP 8X including Fast Writes and sideband
addressing
• Flip-chip BGA packaging*
```[http://www.nvidia.com/object/LO_20021117_4942.html](http://www.nvidia.com/object/LO_20021117_4942.html)
And other headlines like: POWERED BY PURE ADRENALINE
ENGINEERED WITH A PASSION FOR PERFECTION
CINEMATIC EFFECTS BEYOND IMAGINATION
UNLEASH THE EXPERIENCE
GAMING NIRVANA!

But I cannot find out how much power the FX5200 needs. The Optiplex GX520 mini tower only supplied 10 watts to its PCI Express 1.0A slot, but none of the GX520's say how much power they supply to their PCI slots. When I installed an AGP FX 5200 in an HP PC from 2004, its overrated OEM 250w PSU could not even boot (your PSU is rated 220w), even though measured AC input was 130w total max after upgrading its PSU to a better 330w, which handled subsequent upgrades to GeForce 6800, and not sure why to ATI X1300. A Dell desktop (Inspiron?) at work from the same era booted fine with the FX5200 when testing that. So I cannot tell you what might work for a PCI (non-express) graphics card, just that even if it was the tower model with PCI-E 1.0A it would be tough to find a decent graphics upgrade that ran on 10 watts.

---

### Post by bronxio on 2017-02-20
I didn't know either, but yes, I can guarantee you that it is a PCI version, although nVidia may would denied it :D You can check it out in the [eBay page]("http://www.ebay.es/itm/272475976666?_trksid=p2057872.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT") where I bought it.

The thing is that it works perfectly with no failure at all in Windows, and it works with Ubuntu 10 as well in this very computer... so, not a power problem, I guess.

---

### Post by bronxio on 2017-02-25
Ok, solved. Just in case someone google this or something:

I created a bootable pendrive in dd mode with Rufus (instead of ISO, but with the official ISO image, because the Rufus program let to choose that option) and, when I boot it, I selected the install option directly instead of try/live one. I attached another monitor to the DVI port as well this time (before there was only one connected to the VGA). I don't know what of this three things solved my problem.

I changed some things in BIOS, but I didn't mention them because I'm sure that I haven't touched anything related with video. If I'm wrong, then I guess that it was a power problem (but Dell creates very simple BIOS menus, there was nothing special there)

---

