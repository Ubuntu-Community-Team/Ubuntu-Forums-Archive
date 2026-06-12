---
title: "X-Server doesnt start"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by dcahrakos on 2005-04-18
Well, Ive gotten past the "starting hotplug subsystem" just to see if it will start up, then ill see whats wrong from there...but then I get an error, about the x-server not being able to start, so I posted in a thread made by someone else, and was told if I had an onboard video, and another video card, that it probably is the problem, so im wondering, how would I make ubuntu only detect the other video card i have, which is an ati RADEON 9250 128MB....? I tried to reconfigure, but I just made it not work even more...and now cant access anything, just stays black, but ill reinstall everything, if theres a way to get it to work.

---

### Post by kassetra on 2005-04-18
[QUOTE=dcahrakos]Well, Ive gotten past the "starting hotplug subsystem" just to see if it will start up, then ill see whats wrong from there...but then I get an error, about the x-server not being able to start, so I posted in a thread made by someone else, and was told if I had an onboard video, and another video card, that it probably is the problem, so im wondering, how would I make ubuntu only detect the other video card i have, which is an ati RADEON 9250 128MB....? I tried to reconfigure, but I just made it not work even more...and now cant access anything, just stays black, but ill reinstall everything, if theres a way to get it to work.[/QUOTE]

In the bios, have you disabled the onboard video card?

---

### Post by dcahrakos on 2005-04-18
[QUOTE=kassetra]In the bios, have you disabled the onboard video card?[/QUOTE]
 I checked, and I dont specifically see an option to disable it, but there are options to set how much memory it has, and an option to pick which one to boot up with, and the one for booting up is PCI cause thats where my video card is.

---

### Post by alastair on 2005-04-18
I believe that X will probe PCI ID's, and you can also specify a card's PCI ID in the Xorg.conf file. This /might/ be something worth investigating if you are concerned about multiple cards being present.

---

