---
title: "Can Ubuntu 10.04 handle 3 monitors?"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by rlischer on 2010-08-11
I was running Ubuntu fine with 2 monitors, I added another video card and a 3rd monitor, and now it only shows up on one.  All 3 work fine when I boot to Windows 7.

Can Ubuntu do all 3 or not?

Thanks

---

### Post by MSPdwalt on 2010-08-11
What are your 2 graphics cards?

Do they show up in the configuration app? (example the Nvidia X Server settings?)

I know when I setup dual displays with my Nvidia card it chose one as the primary and I had to enable and set the resolution and such on the other.  I would assume addidng a third would require a similar process.

-DW

---

### Post by rlischer on 2010-08-11
> **MSPdwalt said:**
> What are your 2 graphics cards?

Do they show up in the configuration app? (example the Nvidia X Server settings?)

I know when I setup dual displays with my Nvidia card it chose one as the primary and I had to enable and set the resolution and such on the other.  I would assume addidng a third would require a similar process.

-DW

Both Cards are ATI, I added an ATI 2400 and it's the only one that shows up.  The one that did work, (ATI 9800) now says unknown in the ATI Catalyst Control Center.  So the ATI Catalyst Control Center now sees a 2400 and an unknown.  I told it to use the unknown, but after a reboot, Ubuntu does not load.  Had to load in failsafe video mode.

---

### Post by MSPdwalt on 2010-08-15
Have you tried re-installing the ATI drivers?

---

### Post by rlischer on 2010-08-15
> **MSPdwalt said:**
> Have you tried re-installing the ATI drivers?

I'll try that, thanks

---

