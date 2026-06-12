---
title: "Booting into safe graphics mode?"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by John Read on 2008-02-20
Hope someone out there can help.

I've got Ubuntu 7.10 (Gutsy) running on a new Toshiba laptop. It's using a very recent graphics card that I've given up on trying to configure in Ubuntu (I'll just wait for Ubuntu 8.04).

The hassle is that my laptop usually boots into Vesa mode which  can live with, but sometimes it just hangs and I have to restore my xorg.conf file with a backup I made earlier and try again.

Is there something I can insert into the xorg.conf file to stop it searching for a graphics driver at boot time and just go straight to Vesa?

Thanks in anticipation.

John R.

---

### Post by zvacet on 2008-02-21
system>admin>restricted driver(or device I´m not sure because I don´t use english version) manager look if you can find driver for your card.

---

### Post by John Read on 2008-02-22
Thanks for your advice. No drivers yet available.
Regards,  John R.

---

### Post by PmDematagoda on 2008-02-22
What is the specific VGA card you are using?

---

### Post by John Read on 2008-02-23
The graphics card I am using is ATI Mobility Radeon HD 2600.

It seems to me that the "Mobility" driver is the problem as I can locate Linux drivers for ATI Radeon HD 2600.

Thanks for your assistance in this.

Regards,

John R.

---

