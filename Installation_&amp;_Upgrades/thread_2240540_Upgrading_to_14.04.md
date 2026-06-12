---
title: "Upgrading to 14.04"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by gulmer on 2014-08-20
When upgrading to 14.04 from 12.04 with update manager I get this warning: Your graphics hardware may not be fully supported in Ubuntu 14.04.

Running the 'unity' desktop environment is not fully supported by your graphics hardware. You will maybe end up in a very slow environment after the upgrade. Our advice is to keep the LTS version for now. For more information see [https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D) Do you still want to continue with the upgrade? 

Looks like I need a new graphics card. If that's so, which card is best/supported with 14.04 release? Right now the card in this computer is a GeForce 7200 GS.

---

### Post by papibe on 2014-08-20
Hi gulmer.

Were you using the Nvidia proprietary driver?

The most common case is that the latest Nvidia driver doesn't support old Nvidia cards (usually below 8xxx series). In my understanding, the Nvidia open source driver, nouveau, should be able to support your card just fine.

If you have the budget to upgrade, almost any mainstream Nvidia card would do. Don't get the lastest, newer, pricey ones though.

On the budget side you can get a 210, for instance. In the midrange something like a 640 or a 750Ti.

Let us know if you need help uninstalling the proprietary driver and setting nouveau.
Regards.

---

### Post by gulmer on 2014-08-29
Just bought a new graphics card, EN210 and that did the trick.

---

