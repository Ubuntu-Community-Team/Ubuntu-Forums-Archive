---
title: "Ungrade Ubuntu will it keep drivers."
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Scrib on 2007-10-21
I've spent a lot of time getting my Ubuntu 7.04 working with my graphics card and wireless card. I solved my graphics card problems by using ENVY to install the graphics card drivers.

I made a CD from the 7.10 ISO and booted from it and the screen went blank after a minute or so. The exact  same problem I had when I first installed my Graphics card on my Ubuntu 7.04 build, so it looks like 7.10 STILL doesn't have the drivers from my card "out of the box".

I assume I can boot my Ubuntu 7.04 build  as normal and then run the 7.10 CD which will start an upgrade ????? If so will this upgrade keep my Graphics card driver/settings or will I have to go dow the ENY road again??

---

### Post by por100pre1 on 2007-10-22
In order to do an upgrade you have to remove the driver added with Envy. From the [Envy webpage]("http://albertomilone.com/nvidia_scripts1.html"):

> WARNING: you will have to remove the driver you installed with Envy before upgrading Debian or Ubuntu to a newer release (e.g. upgrading Ubuntu Edgy to Ubuntu Feisty or Debian Etch to Debian Lenny)

IMHO, there's no need to upgrade to Gutsy at this time, Fiesty will be supported for a long time. Enjoy your existing installation.

---

