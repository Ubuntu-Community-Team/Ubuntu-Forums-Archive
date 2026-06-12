---
title: "IPW3945 LED dead"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2008-10-10
During todays kernel upgrade my wlan LED went off and seems to be dead (booting Windows didn't help). Coincidence? Is it even possible that some Linux voodoo could have hurt the LED?

---

### Post by beartard on 2008-10-10
> **MacUntu said:**
> During todays kernel upgrade my wlan LED went off and seems to be dead (booting Windows didn't help). Coincidence? Is it even possible that some Linux voodoo could have hurt the LED?
Is this a mini-pci card for a laptop?  I remember that earlier versions of the driver had to have an explicit declaration in the module's settings to use the LED.  I seriously doubt anything having to do with Ubuntu could've hurt the LED itself.

---

### Post by MacUntu on 2008-10-11
> **beartard said:**
> Is this a mini-pci card for a laptop?  I remember that earlier versions of the driver had to have an explicit declaration in the module's settings to use the LED. 

Yes and no, I had never to declare anything, it always worked.

> **beartard said:**
> I seriously doubt anything having to do with Ubuntu could've hurt the LED itself.

Really strange. SMD soldering is not one of my expertise so I guess I have to stay with it.

---

### Post by MacUntu on 2008-10-11
Luckily you were wrong. Latest acpi-update reanimated the LED (Linux and Windows). Seems the LED got disabled device-sided.

I'm happy! :-)

---

### Post by gnomeuser on 2008-10-11
[You mean you have network on one of those](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269931) - you lucky badboy.

---

### Post by MacUntu on 2008-10-11
I really don't understand it as I've never had any bigger problems with this card. :neutral:

---

### Post by gnomeuser on 2008-10-11
> **MacUntu said:**
> I really don't understand it as I've never had any bigger problems with this card. :neutral:

Me neither, but this is a long standing issue for me, the last place this worked was with the kernel that got issued with F9. Hardy didn't work when I tested it, Intrepid never worked. So now I have a usb dongle (Belkin something or another) it works for me.

The card isn't broken, which would be an obvious concern.. I mean it's intel, they are very supported. It should work, yet it doesn't.

What frightens me the most is the lack of follow up on a report like that, network is kinda nice to have, especially since working network and apt-get means we can fix most other issues with an update thus it should probably be high priority.

---

### Post by beartard on 2008-10-11
Glad you got it fixed!  My current laptop has that card in it and I can't remember if it has had LED problems or not.  I was confused with my older laptop which had an ipw2100 in it.  Its driver needed a "led=enabled" thing when modprobing it.  Sorry for my confusion.

---

### Post by MacUntu on 2008-10-15
Oh da**it. Todays updates disabled it again. At least I now know it's no hardware defect.

---

