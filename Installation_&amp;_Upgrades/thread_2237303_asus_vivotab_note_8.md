---
title: "asus vivotab note 8"
date: 2014-08-01
forum: Installation &amp; Upgrades
---

### Post by ivo-welch on 2014-08-01
has anyone managed to boot ubuntu (or any linux) natively [not virtualized] on an asus vivotab note 8?

it's one of the reasonably new and cheap windows 8 tablets (with digitizer).

---

### Post by jamessnell on 2014-10-09
I'm very interested in this as well. I see no reason for it not to work, it's just another x86 machine. The main question I have is does X suck in the usual ways and how about the touch interface? Being a wacom, I wager it'll work out of the box. I'll be trying this when I finish saving my empties and finally order myself one of these bizarre little rigs. I'm also fantasizing about putting OSX86 and Windows 10 on one. Not to mention there are 128GB microSD options now. Yeah yeah, they *claim* the max capacity is 64GB, but that's the kind of thing that they decide based on what they've tested it with.

---

### Post by Vladlenin5000 on 2014-10-09
> **jamessnell said:**
>  it's just another x86 machine.

Actually no, it isn't. 
Intel® Atom™ Z3740 Quad-Core, 1.86 GHz is a 64-bit CPU for which too many vendors already bundled a 32-bit UEFI making things way harder than they should be, and that is just to boot the installation media, let alone everything else*.

* Expect certain devices to NOT work: Touchscreen, WiFi (requires SDIO support before it can be detected, then finding a working driver...), Bluetooth (for the same reason as WiFi), sensors, ...

---

### Post by jamessnell on 2014-10-09
> **Vladlenin5000 said:**
> Actually no, it isn't. 
Intel® Atom™ Z3740 Quad-Core, 1.86 GHz is a 64-bit CPU for which too many vendors already bundled a 32-bit UEFI making things way harder than they should be, and that is just to boot the installation media, let alone everything else*.

* Expect certain devices to NOT work: Touchscreen, WiFi (requires SDIO support before it can be detected, then finding a working driver...), Bluetooth (for the same reason as WiFi), sensors, ...

... Wow. I hope you're mistaken. Else my interest in the x86 platform just got sliced in half. It may be reasonable to boot other platforms by installing an alternate Windows bootloader, I have a specific one in mind but can't think of the name right now "BCD" being in the name. I guess efi could be navigable too. Heh, maybe we need a uboot port to x86 efi. (*vomits within mouth*)

---

