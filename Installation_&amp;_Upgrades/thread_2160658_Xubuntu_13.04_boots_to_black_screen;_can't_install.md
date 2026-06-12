---
title: "Xubuntu 13.04 boots to black screen; can't install"
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by Maximus559 on 2013-07-07
I'm trying to install Xubuntu 13.04 on a Compaq Presario SR1215CB desktop. I've tried both with a flash drive and an external DVD drive, and keep getting the same problem.

When I select the "Try Xubuntu without installing" or "Install Xubuntu" option, I get a basic loading screen with the Xubuntu logo, some flashing dots, and no background image. Then I get a black screen and "no signal" message on my monitor, and nothing happens until I do a hard reboot.

This machine has an Asus A7V8X-LA motherboard with a Via KM400A chipset and Via UniChrome integrated graphics. It works with Windows and other Linux distros, so I assume the machine is physically sound. Any ideas? I suspect that the Openchrome drivers are to blame... perhaps a super-secret boot option would do the trick?

---

### Post by Maximus559 on 2013-07-09
Can anyone confirm *buntu 13.04 running on a machine with the UniChrome IGP?

---

### Post by Maximus559 on 2013-08-04
Problem solved. Turns out Xubuntu was auto-detecting the wrong screen resolution and / or refresh rate, resulting in a black screen. Booting with another monitor did the trick.

---

