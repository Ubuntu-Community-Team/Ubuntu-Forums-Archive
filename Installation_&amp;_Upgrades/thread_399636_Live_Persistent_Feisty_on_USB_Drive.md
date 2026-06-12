---
title: "Live Persistent Feisty on USB Drive?"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by Seryll on 2007-04-02
Hey, I was wondering if Feisty would work as a live persistent USB Drive like Edgy and Knoppix and what not. I followed the steps most of the way as if I was making a persistent edgy, but the persistence seems to be the problem. it boots up fine from the USB and through the custom live which is supposed to be persistent, but when I reboot the USB and go back into my persistence mode, it acts as if it's still just live, no changes are left the same. I'm guessing casper-rw as the second partition doesn't work anymore. Any suggestions?

---

### Post by dcstar on 2007-04-03
> **Seryll said:**
> Hey, I was wondering if Feisty would work as a live persistent USB Drive like Edgy and Knoppix and what not. I followed the steps most of the way as if I was making a persistent edgy, but the persistence seems to be the problem. it boots up fine from the USB and through the custom live which is supposed to be persistent, but when I reboot the USB and go back into my persistence mode, it acts as if it's still just live, no changes are left the same. I'm guessing casper-rw as the second partition doesn't work anymore. Any suggestions?

Search for usbpendrive.

---

### Post by gyterpena on 2007-04-05
There is a bug see[ here ]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591")

---

