---
title: "I forgot to turn WLAN on during the install"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by CSMatt on 2007-01-30
My laptop comes with a toggle switch to turn on or off wireless LAN.  When I installed Edgy, I forgot to turn it on so that the install process would detect the card.  Now, it just isn't detected by the installation when it's on (although I don't think I tried rebooting yet), and the wireless light is off even if the switch is on.  Does this mean I have to install Edgy all over again?

---

### Post by Cueball696 on 2007-01-30
yes. had the very same problem

---

### Post by jonobo on 2007-02-09
You definitely don't need to re-install Ubuntu to get your WLAN running.

But you need a driver for your WLAN-Card.

Which driver you need depends on the Chip on your WLAN-Card.

Google for the name of your WLAN-Card plus the word "chip" or so.

Or open a console, type
```
lspci
```
hit Return and post the output here.

---

