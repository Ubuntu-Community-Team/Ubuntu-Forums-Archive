---
title: "Please Broadcom out of the box !"
date: 2009-01-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by *g!t5^_)*(H on 2009-01-11
Hi,

I'm happy to read :

[http://mobile.slashdot.org/article.pl?sid=09/01/11/0726249](http://mobile.slashdot.org/article.pl?sid=09/01/11/0726249)

Does this mean than, Broadcom wireless will com with Jaunty out of the box without activate propietary firmware ? 

Please, after several years of bad wireless hacks, Broadcom users (me) want to use wireless without special configuration, specially from Live CD.

---

### Post by Mazza558 on 2009-01-11
If this is true, it's great news. There's nothing more fiddly than having to save a guide and the drivers to USB in order to install them using nidiswrapper - if your PC is upstairs and is a desktop, there's no chance of running a 20m long ethernet cable around the house.

---

### Post by LordVeovis on 2009-01-11
I dislike having to connect my laptop by wire to get my wireless to work.

---

### Post by ShirishAg75 on 2009-01-11
Guys, don't jump overboard. The drivers need to be proven. Also at some point what features the driver/drivers will support and which cards they will support needs to be worked out. Its still going to take it own time, there is possibility that ubuntu does include it sometime soon.

Looked up at the mailing list and these cards are supposed to have been used to test and make those drivers. 

> 

Belkin PCMCIA 4306 card,
Siemens PCI 4306 card.
Belkin PCI 4306 card.
ASUSTeK PCI 4318 card.



[https://lists.berlios.de/pipermail/bcm43xx-dev/2009-January/008471.html](https://lists.berlios.de/pipermail/bcm43xx-dev/2009-January/008471.html)

---

### Post by Slug71 on 2009-01-11
I have Broadcom and i dont have the proprietary enabled and works fine. Has since i started using Jaunty in Alpha 1.

---

### Post by Ayuthia on 2009-01-11
I tried it out with my 4311 rev 01 card and it works with it also.  My guess is that it will be a while before it becomes packaged with anything.  It doesn't support encryption yet either and at this point, it is still borrowing some firmware from the proprietary side.

It was nice to see that pop up on the b43 mailing list and it was even more exciting to see my laptop connect wirelessly with it!

---

### Post by Ayuthia on 2009-01-14
The group has just made another update to the firmware so that it now supports WPA2 and they are also packaging the initval files (no need for b43-fwcutter!):
[http://www.ing.unibs.it/openfwwf/](http://www.ing.unibs.it/openfwwf/)

---

### Post by Eclipse. on 2009-01-14
Broadcom is already supported out of the box.

System..Administration..Hardware Drivers..Tick Box..Reboot...Done

I doubt that driver will be included as it doesnt support enough devices.In all honesty though I have always used ndiswrapper and never touched the firmware or b43 driver.Ndiswrapper has always worked with me and gave a good performance.

---

### Post by Mazza558 on 2009-01-14
> **Eclipse. said:**
> Broadcom is already supported out of the box.

System..Administration..Hardware Drivers..Tick Box..Reboot...Done

I doubt that driver will be included as it doesnt support enough devices.In all honesty though I have always used ndiswrapper and never touched the firmware or b43 driver.Ndiswrapper has always worked with me and gave a good performance.

Out of the box means that it works straight away, with no prior internet connection.

---

### Post by Ayuthia on 2009-01-14
> **Eclipse. said:**
> Broadcom is already supported out of the box.

System..Administration..Hardware Drivers..Tick Box..Reboot...Done

I doubt that driver will be included as it doesnt support enough devices.In all honesty though I have always used ndiswrapper and never touched the firmware or b43 driver.Ndiswrapper has always worked with me and gave a good performance.

The wl module provides the wireless support through Hardware Drivers and without the internet connection, but it is propietary.  It also only covers the 4311, 4312, 4321, 4322, and some 4328 cards.

As for the new firmware, they have only confirmed that it works for the 4306 and 4318 cards, but it is possible that it will work for other cards too (hopefully it will cover all the cards that b43 uses).  That is why they are looking for people to test it.

I have a 4311 rev 01 and I was able to use the firmware with the b43 module.

I am hoping that they can get a lot of testers involved so that the firmware can be released in the near future.

---

### Post by Cenotaph on 2009-01-14
Good news, i have a bcm4318 and although im kinda used to installing the firmware everytime i install a linux distro i was already wondering when we would get the needed firmware out of the box. seems like the first step is done, kudos :)

---

