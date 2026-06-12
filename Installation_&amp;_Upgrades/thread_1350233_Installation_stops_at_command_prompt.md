---
title: "Installation stops at command prompt"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by cyaneo on 2009-12-09
Hi

I want to install ubuntu 9.10 desktop amd64 from CD-ROM to a fresh HDD.

-After the language page the menue comes up and I choose "install to disk".
-The installer starts and runs for a few minutes.
-Then the installer hung for a while (2-3 min.) at ieee1394:host added:BUS [0-0blah] (nothing connected)
-After this, the ubuntu logo comes up, a frew lines scrolls up and I'm landing at the command prompt (ubuntu@ubuntu$).
-After this, the PC turns to a endless blank screen...

A reboot show me, that nothing was installed.


My System:
GA-EG45M-UD2H
Core2Duo E6400
4x2GB Kingston KHX64000
Samsung HDD 320GB HM320JI

---

### Post by darkod on 2009-12-09
Do you have any firewire devices? 1394 is firewire. It seems it gets stuck there.

---

### Post by cyaneo on 2009-12-09
Firewire only was activated at the MB-BIOS, but nothing connected, **so I disabled FireWire Support on my mainboard.**
Now the installer hungs at uhci_hcd,** so I disabled USB 2.0 Support on my mainboard.**
Now the installer hungs at RTL8168d/8111d at 0xffffc90000c4600 IRQ 28, **so I disabled onboard LAN ****on my mainboard.**
Now the installer hungs at usbhid: v2.6:USB HID core driver, [B]so I disabled USB 1.1 Support on my mainboard.
[/B]Now the installer hungs at RSP <ffff8802355f9c80> CR2: 0000000000000000 [2.671363] ---[end trace 07be427dbf6ea7ab]---, **so I disabled ubuntu and enabled Windows 7.**

This was a pretty short excursion to the ubuntu Desktop Edition.

---

