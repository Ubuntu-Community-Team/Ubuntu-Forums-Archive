---
title: "[SOLVED] sata drive isn't detected.. :("
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by epidemiks on 2008-10-10
Ok, so a mate and I are building a mythbuntu box.
Build went fine, everything squeezed into the nice Antec Fusion case, and we nearly lost our s*** when the Antec remote took control of the cursor without any config in the liveCD :)
The problem is however, we can't get the install to see the 640Gb SATA hdd??!! Actually, we can't get it the bios to even see it.

I've not dealt with sata drives before, and we tried every bios combination we could till 2am last night, so we figured we'd sleep on it.

Here's what we know:
- sata DVD rw works on either of the two sata cables, and is detected by bios and boots live cd fine.
- 2nd brand new sata hard drive on either of the two sata cables does not get detected either.
- every combination of Sata> Ahci/Native IDE/Legacy IDE/Raid etc in bios still will not detect in bios
- vista (blarg!) cd does not find hdd during setup either

Any advice to get this happening will be very much appreciated!

---

### Post by epidemiks on 2008-10-10
Going out on a limb here... could both brand new hard drives be duds?

also, these drives didn't come with any jumpers set, nor is there info what master/slave jumper settings in the documentation..

---

### Post by cariboo on 2008-10-11
If there is an ACHI setting in the bios you may need to change it to ACHI. If it is set to the defaults it is probably trying to emulate and ide drive.

Jim

---

### Post by epidemiks on 2008-10-11
> **cariboo907 said:**
> If there is an ACHI setting in the bios you may need to change it to ACHI. If it is set to the defaults it is probably trying to emulate and ide drive.

Jim

Jim, there's a SATA>ACHI option in bios, but had no luck using that so far..

the other drive worked with jumpers, but this one (Samsung HD642JJ) only has 4 pins for jumpering, and no combo helps there either :confused:

---

### Post by epidemiks on 2008-10-11
Ahh. Solved.
It seems one of the power cables on the HD's power lead was loose.
Thats what you get with Shaw PSU's! lol

---

