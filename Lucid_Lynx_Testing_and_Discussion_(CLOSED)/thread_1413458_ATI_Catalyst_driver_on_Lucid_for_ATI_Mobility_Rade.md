---
title: "ATI Catalyst driver on Lucid for ATI Mobility Radeon HD 4570"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by janderpola on 2010-02-22
I´ve installed Lucid on my laptop, because is the only version of Ubuntu that works with my Wifi and sound, but when I try to search for ATI propietary drivers, it doesn´t find any.

It found it on Karmic, and the problem is that with open-source driver the graphics card fan it makes a lot of sound, and this didn´t happen in Karmic (with Catalyst driver).

Why is there no driver (propietary) for ATI on Lucid? Any way to make it work?

---

### Post by littlesatan on 2010-03-07
No way, bro -- ATI hates us.

---

### Post by linux4life88 on 2010-03-07
The fan is really loud because it is not throttling down your graphics card. Right now this can only be done through the proprietary drivers. Karmic has Xorg 7.4 and Lucid has Xorg 7.5, from what I understand. If this is correct then the newest version of the ATI drivers only support up to Xorg 7.4, aka Karmic. Most likely Xorg 7.5 won't be supported until Lucid is released.

---

### Post by tiger2wander on 2010-03-26
Try out newest version of ATI propietary drivers 10.3...
I'm trying it but no luck :(, may problem come from I have upgraded from karmic and my old ATI propietary is not removed correctly (still have it in dpkg-query -l but can not remove :( )
One more thing, I was can not buildpkg for lucid use ati-driver-installer-10-3-x86.x86_64.run

If you are interest, try to get it from: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Best regard!

---

