---
title: "Kubuntu 16.04 live DVD hangs on splash screen"
date: 2016-06-08
forum: Installation &amp; Upgrades
---

### Post by jared28 on 2016-06-08
Hi 
I'm trying to try out Kubuntu 16.04 on my PC, and when I load it, the progress bar always stops at a certain point. I've left it for an hour with no change. I did a checksum before I burned the disk, so I know it's not a corrupt file.

Computer specs:
AMD FX 6 core processor
16GB DDR3 RAM
240GB SSD
1TB HDD
NVidia GeForce 560 SE graphics card

Any help would be greatly appreciated! Thanks

---

### Post by X-RED_Tech on 2016-06-08
Your graphics
> **jared28 said:**
> NVidia GeForce 560 SE graphics card
is the most probable cause.
Try nomodeset (F6 > nomodeset in the initial menu).

---

### Post by jared28 on 2016-06-10
That was it! I should have known that. I got it installed and we're all good now. Thanks for your help!

---

### Post by X-RED_Tech on 2016-06-10
You're welcome.
I just need to add the nomodeset is a temporary solution. It uses the standard VESA (low resolution graphics), compatible with everything, so you have a desktop. You should then install the recommended proprietary drivers in Additional Drivers.

---

