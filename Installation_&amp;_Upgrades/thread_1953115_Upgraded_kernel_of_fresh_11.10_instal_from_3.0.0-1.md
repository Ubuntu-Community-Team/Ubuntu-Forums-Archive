---
title: "Upgraded kernel of fresh 11.10 instal from 3.0.0-12 to 3.0.0-17. Can't boot into *17."
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by thealmightyone on 2012-04-05
Hardware first, as from what little I know, this could be the issue:
[LIST]
[*]Motherboard is [this]("http://www.asus.com/Motherboards/AMD_CPU_on_Board/E35M1I_DELUXE/"), an AMD fusion APU (E-350 AND HD6310].
[*]Hard drive is [this]("http://www.kingston.com/us/support/technical/products?model=SS100S2") (8GB variant), an 8GB SSD (with latest firmware).
[/LIST]

So, this is a little HTPC I'm putting together (I have a larger HDD for data, not yet installed). I installed Ubuntu 11.10 of a USB (mounted using unetbootin), which I've done dozens of times on other hardware, but never before this setup. After the successful install, I downloaded all updates **except** for kernel updates, so I was left with a fully updated Ubuntu with a 3.0.0-12 kernel.


I then upgraded to 3.0.0-17. When I boot into this kernel, the system reboots very shortly after the GRUB screen - it only shows a black screen, no purple to suggest it made it into the GUI.

If I boot into 3.0.0.17 recovery mode, two lines appear straight after GRUB:

> Memory mode boot
Loading initial ramdisk

After a second or so, the system goes to a black screen, then reboots.

**However** I can boot into 3.0.0-12 perfectly fine; I've even installed the latest ATI drivers, which went perfectly, and have restarted to check they work.

Anyone got any ideas as to why I can't boot into 3.0.0-17?

---

### Post by Frogs Hair on 2012-04-05
There have been problems reported with 3.0.0-17 although I didn't have any and now have the -18 kernel via proposed updates. Search for the other threads they may point you in the right direction. If -12 works use it. 12.04 will be out in 21 days anyway if you were planning to install it.

---

