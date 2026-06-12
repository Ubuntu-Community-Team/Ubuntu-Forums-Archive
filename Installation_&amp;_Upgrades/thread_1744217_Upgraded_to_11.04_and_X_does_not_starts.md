---
title: "Upgraded to 11.04 and X does not starts"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Swordlong on 2011-04-30
Hi!

After upgrading to Ubuntu 11.04 I only get the text mode login. I have a ATI Radeon HD 3600 card and before upgrade I used the propiertary driver (to make the dual screen mode work).

I have tried to download the driver again from ATI and installed that but it does not helped. 

I have put the Xorg.0.log and some other outputs in [http://83.251.70.81/X/](http://83.251.70.81/X/)

Would be very glad if someone could guide me trough this.

---

### Post by dino99 on 2011-04-30
use the package(s) from synaptic, not the Ati ones

sudo rm /etc/X11/xorg.conf

---

### Post by Swordlong on 2011-04-30
> **dino99 said:**
> use the package(s) from synaptic, not the Ati ones

sudo rm /etc/X11/xorg.conf

I tried to install xserver-xorg-input-synaptics package but it was already installed. I have problem surfing without X11 but googled after synaptic drivers but only found Windows drivers.

Still not working

---

### Post by Swordlong on 2011-04-30
Problem solved. The ATI-driver complained about something about DKMS and proposed a install of linux-headers-2.6.38-8-generic-pae witch made it work. Thanks.

---

