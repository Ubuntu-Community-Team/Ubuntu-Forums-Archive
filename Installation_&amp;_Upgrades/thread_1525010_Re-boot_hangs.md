---
title: "Re-boot hangs"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by choochoo22 on 2010-07-06
A second, odd problem;  after shutting down or re-booting with 10.04, the boot hangs on the BIOS splash screen and does not proceed, ever.  To get past this, the power supply must be switched off, and back on.  The boot then proceeds normally.

This is non-fatal but annoying, any suggestions on how to avoid it?

---

### Post by dino99 on 2010-07-06
i have this issue with one of my system too: reboot dont work (maybe due to some chipset)

---

### Post by WinRiddance on 2010-07-06
On a PC this is a common problem related to network cards ... a problem that sometimes vanishes when the network card is disabled in the bios if you're using WiFi instead. On other computers this sometimes happens with connected USB devices, in particular external USB disks and USB hubs. Briefly disconnect during startup and the problem goes away. Annoying, but nothing major ....

However, that this problem is directly related to the **power supply** is something that I've never encountered in my 19+ years of experience with computers. More than likely it's actually one of the above ...

---

### Post by choochoo22 on 2010-07-06
The network "card" is built into the motherboard and in use, so I really can't disable it on boot each time.  There is no external usb drive or hub.

I doubt it is the power supply itself that is causing the problem but rather something that resets when the power supply is turned off.

---

### Post by WinRiddance on 2010-07-08
A lot of motherboards have built-in network cards ... which can be disabled from within the bios settings. Once it's disabled in the bios it remains disabled until you enter the bios again in order to enable it (unless you've forgotten to save the settings when the bios was being exited in which case nothing will change when you reboot the machine).

---

