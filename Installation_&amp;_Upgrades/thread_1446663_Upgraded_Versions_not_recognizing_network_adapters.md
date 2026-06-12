---
title: "Upgraded Versions not recognizing network adapters"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by punkarea51 on 2010-04-04
I was using Ubuntu 8.x (can't remember the exact version) on my netbook. I had downloaded Kubuntu 10.04, but the network manager wouldn't recognize my wireless card and would not connect to a land line. I subsequently downloaded Ubuntu 10.04 and then 9.10 only to have the same problems. 

Under hardware drivers, it lists:

Broadcom b43 wireless driver
Broadcom STA wireless driver


I have tried to activate and install both of these with no luck. Clicking activate for the B43 driver does nothing. I  Clicking activate for the STA driver will cause it to download and install and tell me to reboot; however, after rebooting the driver wasn't installed or activated. Now, trying to activate either driver just causes my system to freeze.

When I do ifconfig, the only sources listed are:

eth0
lo

When I do iwconfig, it says that there was nothing located.

Neither of which are tagged with claimed, unclaimed, enabled, disabled.

---

### Post by punkarea51 on 2010-04-04
I've messed around with it a bit more, but have had no luck. When I try to ping, I get an error. It seems like I may be missing drivers. I have the drivers CD that came with it, but I can't seem to get the CD image to read from a flash drive properly. I've tried UNetBootin and copying the disk contents straight over.

---

### Post by leorolla on 2010-04-13
Can you get wired connection?

Could you post the output of ```
lcpci
```?

---

