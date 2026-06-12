---
title: "Upgrade to 15.10: The UPS is critically low. The computer is about to shut down."
date: 2015-10-22
forum: Installation &amp; Upgrades
---

### Post by mniland on 2015-10-22
Upgrading from a fresh 15.04 install to 15.10, I got a notification containing the message in the title. The computer proceeded to shut down in the middle of the upgrade process, leaving me "unable to mount root" on next boot. The UPS (an APC 750) had full battery and active A/C power.

---

### Post by thomass3 on 2015-11-09
I at least was able to mount, it tried to boot 15.10 but the login screen just returns after attempting to login. On another terminal I am trying to repair the install by continuing dpkg.

Edit: Seems to be working now.

---

### Post by Edward_Diener on 2016-02-09
> **mniland said:**
> Upgrading from a fresh 15.04 install to 15.10, I got a notification containing the message in the title. The computer proceeded to shut down in the middle of the upgrade process, leaving me "unable to mount root" on next boot. The UPS (an APC 750) had full battery and active A/C power.

I can confirm the exact same problem. I have an APC Back-UPS XS 1500. Is there a workaround to this upgrade problem ?

---

### Post by SeijiSensei on 2016-02-09
What if you plug the machine directly into the wall outlet?

---

### Post by Edward_Diener on 2016-02-23
> **SeijiSensei said:**
> What if you plug the machine directly into the wall outlet?

I did something similar to what you suggest to get around this problem when upgrading. I simply disconnected the USB connection between my power supply and my computer which told Ubuntu that my computer was connected to a power supply, before upgrading. This way Ubuntu 15.04 was not picking up the power supply at all even though it was there, so it did not shut down the computer during the upgrade with the reported bug in the OP. After the upgrade to 15.10 I was able to connect the USB connection again, Ubuntu picked up the power supply being attached, and all is well.

---

