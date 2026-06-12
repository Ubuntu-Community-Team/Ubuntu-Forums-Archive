---
title: "Installing Ubuntu on a Dell XFR D630"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by Dark_Rider2k3 on 2013-05-22
So recently my mom's boyfriend had gave me a Dell XFR Rugged laptop. It's one of those military-grade laptops with the shock-proof hard drives. It came preloaded with windows vista (yuck!) but the original hard drive died and I got it in an attempt to fix it.

I got the new hard drive installed fine in the computer, and it shows up in the bios, but I can't seem to get it working.

I first noticed that Ubuntu loads just fine from the install CD (using 12.0.2 64 bit), but does not show the hard drive. I tried messing with some settings in bios (AHCI mode mainly) but there really isn't that many settings to choose from... leaving me stuck there..

I then tried windows XP. It showed the hard drive, but was unable to format the drive or edit it. It would let me install, however, as soon as I pressed enter for it to install I got a BSOD.

My last attempt was at installing windows vista. Vista also showed the hard drive, but told me in the install that the drive could not be accessed.

Does anyone know how I can get this to work? I'm so stumped.. and just want to get Ubuntu on this thing already...

Thanks a lot for reading this!!!!

---

### Post by Bucky Ball on 2013-05-22
Boot from the LiveCD and launch Gparted. Does that show the drive? If so, format it as an EXT4 partition (it needs to be unmounted to do this; right click>unmount). See if it is recognised by the rest of the system then. 

When you get to the partitioning part of the Ubuntu install hit 'Something Else' and partition the disk as you like it then.

---

### Post by Dark_Rider2k3 on 2013-05-22
> **Bucky Ball said:**
> Boot from the LiveCD and launch Gparted. Does that show the drive? If so, format it as an EXT4 partition (it needs to be unmounted to do this; right click>unmount). See if it is recognised by the rest of the system then. 

When you get to the partitioning part of the Ubuntu install hit 'Something Else' and partition the disk as you like it then.

Gparted does not show the drive.

---

### Post by Dark_Rider2k3 on 2013-05-25
bump for help.. still can't figure this out..

---

