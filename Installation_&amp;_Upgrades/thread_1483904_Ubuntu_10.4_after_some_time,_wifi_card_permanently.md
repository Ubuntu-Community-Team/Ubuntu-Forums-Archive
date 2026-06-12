---
title: "Ubuntu 10.4: after some time, wifi card permanently loses connection (needs reboot)"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by puccio on 2010-05-15
Hi,

I upgraded from Ubuntu 9.10 to Ubuntu 10.4. The procedure went fine, what I noticed is that two times, after quite some time I was already using the system and the wireless network had no problems, the card lost its connection to the AP. Trying to reconnect to the WiFi access point gave no success, and instead a simple reboot made it work again.

This just happened two times, so it can't be a coincidence I guess.
My network card is an **Intel Corporation PRO/Wireless 3945ABG**, with the driver **iwl3945**.

Any clue?

Thanks a lot in advance.

---

### Post by Orel Hazard on 2010-08-08
Same problem here.  Super annoying.

---

### Post by claracc on 2010-08-08
There is a problem with gnome network manager and Intel Corporation PRO/Wireless 3945ABG (you van see in launchpad bugs reported), at least in karmic koala. I recommend to install wicd instead of gnome network manager to manage the wifi.

Wicd is in the repositories so you can use synaptic, in karmic koala when you install wicd, gnome network manager is automatically uninstalled.

---

