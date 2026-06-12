---
title: "Some USB problem i presume"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by STCC on 2007-03-23
When i try to install ubuntu from ubuntu-6.10-desktop-i386.iso it hangs at 90% during the loading module 'usb_storage' for 'usb storage' oem

When i install ubuntu from ubuntu-6.10-alternate-i386.iso everything seems to work fine till it's time to boot up and it hangs on the ubuntu loading screen

When i then boot ubuntu, kernel 2.6.1 - 10  generic (recovery mode) it stops at usbatm_atm_init: atm_start failed: -110!

Any ideas what the problem could be?

---

### Post by tommosimmo on 2007-03-24
Hi There,
I had a similar problem, where Ubuntu would not boot past USB Unuversal Host Controller 3. This was after a PSU upgrade, becuase the old power supply unit had blown. The problem in the end came down to a PCI USB addoncard, which had short circuited and actually blown a capacitor inside the power unit.

Try disabling USB support in the bios, and see if this fixes your problem. If this works, you can try removing individual USB adapters, or think about a new Motherboard.

Hope this helps,
Tom

---

