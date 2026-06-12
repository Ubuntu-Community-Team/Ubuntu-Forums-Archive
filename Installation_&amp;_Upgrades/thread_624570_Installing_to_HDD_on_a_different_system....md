---
title: "Installing to HDD on a different system..."
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by prodezigner on 2007-11-27
I don't know the specifics on the Server Ed. but let's say I have the following scenario:

No optical drive on server (done tried the USB thing, didn't work so hot). But on POS computer there's an optical drive. If I install Server Ed. to the HDD on POS computer, then take the HDD out and put it into server, will it pickup all the hardware or will it be a tedious and painful task to reconfigure everything?

Now... BEFORE you ask... I'm not using an optical drive for one reason. I need both bays of the case to have the removable drive racks (you know, where you just jank out the drive, and throw another one in...)

---

### Post by PmDematagoda on 2007-11-27
If the components of the POS PC differs from the server PC, then it is very likely that your task would be very difficult, the more the POS PC differs from the server PC in terms of hardware, the more difficult your task will be.

---

### Post by nzadLithium on 2007-11-27
I dont think this will work as it will be installed for your other computers processor so your processor module will be wrong which is supposed to be a permanent module so theoretically it shouldn't be able to be done. Get a second opinion coz i am honestly not sure but it seems dangerous to me and i dont think it will work.

I'm unsure about what POS stands for i bet its something simple but i cant be bothered looking it up so excuse me if im asking a dumb question. Cant you jsut take the optical drive out of the POS computer put it in the computer your trying to install on, Install ubuntu then put the optical drive back in the POS computer?

---

### Post by prodezigner on 2007-11-27
I decided to change route...

Check this out..

Case = 50.00
DVD-ROM = 19.00
RAM = 26.00
Removable Drive Rack = 33.00
DVI to VGA Adapter = 4.00 (just for this mobo)
Motherboard = 60.00

TOTAL = 192.00

Where's the HDDs? Well, for the main, I'm using and old IDE HDD... RAM wise it's on spec with Dell's low-end server, if you went with 2GB then it'll run you 42.00 instead of 26 (208.00)

Not bad for a server with some nice features. So a recap of the drive config:

1x SATA DVD-ROM
1x SATA Hot-swap HDD Bay
1x IDE HDD

I have experience with the case I have picked out, very easy to work with, lots of air movement, clean all around and built like a tank. Plus USB and audio connectors on front (what case doesn't now-a-days?) but if I use external media (take a movie on the go with me for example), I can just throw a flash drive in, SSH into my box and transfer it to it.

Plus the way the power supply is, the SATA power leads are VERY short... so having a SATA 5.25 bay works nicely and the IDE works nicely also. with a specific cable and the rest rubber-banded :D

---

