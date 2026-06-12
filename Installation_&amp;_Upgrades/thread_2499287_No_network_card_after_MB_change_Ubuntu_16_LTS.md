---
title: "No network card after MB change Ubuntu 16 LTS"
date: 2024-07-21
forum: Installation &amp; Upgrades
---

### Post by jackson0 on 2024-07-21
Hi,


the mainboard of my Ubuntu 16.04.7 LTS server has failed and I have replaced it with another (newer) one.


The system boots up, but I no longer have a network/internet connection, it seems that the system does not recognize the Intel I219V.


Can anyone help me get the system up and running again? What other information do you need?


Regards,
Jackson

---

### Post by guiverc on 2024-07-21
You do realize Ubuntu 16.04 LTS reached its *end of standard support* years ago.

[https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

Support is now provided by Canonical, who provide ESM or *Extended Support* for certain products beyond the *five years* provided by Ubuntu *community* support.

The kernel choices offered in 16.04 are now very old, given it was the 2016-April (16.04) released, the default was the GA kernel stack, but even if using the *optional HWE* stack you only got a two year newer kernel. If you replaced the motherboard with a newer one, switching to the newer kernel stack maybe a fix (ie. newer kernel modules (aka *drivers*) may help).

This isn't Canonical support don't forget.

---

### Post by him610 on 2024-07-23
One of my machines has an Intel I219V in it. No problems with since I first built in 2018. The correct drivers are in the LTS *buntu distros.
```
$ inxi -NM
Machine:
  Type: Desktop Mobo: ASRock model: H270M-ITX/ac serial: <superuser required>
    UEFI: American Megatrends v: P2.50*** date: 03/16/2018***
Network:
  Device-1: ***Intel Ethernet I219-V driver: e1000e***
  Device-2: Intel I211 Gigabit Network driver: igb
  Device-3: Intel Wireless 3160 driver: iwlwifi
  Device-4: Intel Bluetooth wireless interface type: USB driver: btusb

```

---

