---
title: "&quot;Boot error&quot; - can't boot from 10.04 USB stick on one particular machine?"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by johnnyleitrim on 2010-08-12
Hi,

So I have 32bit kubuntu on my desktop, and want to install 64bit ubuntu since I'm going to upgrade my RAM to 6GB.

I used the "startup disk creator" to load the 64bit ISO onto a USB stick. 

This USB stick will boot 2 of my other machines just fine (which also have 32bit ubuntu), but it won't boot the machine I'm trying to upgrade.  The only message I get when I try to boot is:

"Boot error"

and I must take out the USB and reboot.

I am confused why 2 of my machine will boot fine with the USB stick, and my desktop won't.  The only real difference between the desktop and the other machines is that I used mdadm to create a soft RAID-0 array, but the standard boot partition isn't on that array, so I didn't think it would make any difference.

Does anyone know why I might be getting these errors, or is there any way I can see a log to try and track the error down?

Thanks,
Johnny.

---

### Post by johnnyleitrim on 2010-08-12
Found the solution - was a BIOS setting issue for some reason.  Seems like the default BIOS settings on my particular motherboard stop boots form USB?

[http://www.tomshardware.co.uk/forum/262853-12-intel-d945gclf2-mini-boot-stick](http://www.tomshardware.co.uk/forum/262853-12-intel-d945gclf2-mini-boot-stick)

---

