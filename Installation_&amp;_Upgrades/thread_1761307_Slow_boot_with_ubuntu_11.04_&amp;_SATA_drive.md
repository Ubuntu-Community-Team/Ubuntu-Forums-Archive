---
title: "Slow boot with ubuntu 11.04 &amp; SATA drive"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by roomzeig on 2011-05-18
Hey,
I've just updated to ubuntu 11.04 from 10.04, and my boot time degraded to ~4min on a fresh install. The issue seems to be related to AHCI -- when i disable it in BIOS, the boot time comes back to normal. Actually, this problem already persisted in 10.08 but hasn't bugged me enough to ask around for solution :) 

I'm on a compal JFL92, Core 2 Duo T8300 on Intel 965PM & ICH8, don't know if that matters. 

The only solutions i've found is
 - disable AHCI
 - recompile kernel with / without the sata controller as a module, as described here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448"). 

The first is not an option for me -- when i disable AHCI i run into a whole bunch of other issues -- my keyboard locks every now and then, sound snaps etc. 
I haven't tried the second, but it doesn't seem it's applicable to my problem. my system doesn't freeze for 10secs during boot, it just takes a lot of time to boot.

Thanks for any help!

---

### Post by tedrogers on 2011-07-08
I've got this problem as well. I also have not/do not want to disable ACPI.

I managed to solve the problem, but a recent batch of updates has brought the problem back again.

Any ideas of a solution?

---

### Post by roomzeig on 2011-12-16
hey, try the grub fix described here:
[http://jannepikkarainen.fi/clocksourcejiffies-ja-ubuntu-910-hidastumiset-pois](http://jannepikkarainen.fi/clocksourcejiffies-ja-ubuntu-910-hidastumiset-pois)

worked for me on 10.04, 2.6.32-36-generic. 

What did you do to fix it temporarily?

---

