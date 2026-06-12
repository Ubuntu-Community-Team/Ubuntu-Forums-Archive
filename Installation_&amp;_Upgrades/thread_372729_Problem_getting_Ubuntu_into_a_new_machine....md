---
title: "Problem getting Ubuntu into a new machine..."
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by heroes182 on 2007-02-28
Hi!

I'm building a mini-itx machine (VIA M10000 mobo, 512 ram, 40gb, no optical drive, displaying on a TV as I only have a laptop and no extra monitor), 

Since it has no optical drive, what i'm doing is putting that HD into my laptop, installing from a LiveCD, and then putting the HD back into it. I've tried both Ubuntu 6.10 and 6.06, and both times it worked perfectly fine on the laptop.

The problems start when I put the HD into the new machine...
6.10 makes it as far as the Ubuntu splash screen, but the progress bar never starts. After about 5 minutes, the screen clears itself and it tells me something about Busybox failing.
6.06 works fine until just before the splash screen, but then instead of the splash screen, I just get orange-tinged static. To test whether the problem was just graphic or something else, I let it run for a while, but after 5 minutes, I still hadn't heard the startup sound; I take it this means the whole system is stuck and not simply failing to display properly.

Any help would be greatly appreciated!

thanks

-Tavo

---

### Post by firedrow on 2007-03-08
I seriously doubt this will work successfully.  You have two different architectures, one AMD or Intel and a VIA, different hardware on each, and most likely different video cards on each.  If I was you I would either go out and buy a USB cdrom or find someone with one and use theirs.  The install really needs to detect the hardware and install drivers for that specific hardware.

---

