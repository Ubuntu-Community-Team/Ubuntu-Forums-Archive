---
title: "ubuntu 12.04 heavy distortion after installation"
date: 2013-09-12
forum: Installation &amp; Upgrades
---

### Post by Jiwei_Li on 2013-09-12
Hi guys

I recently try to install 12.04 LTS on my office desktop, which is an APIC machine. I boot from live usb with apic=off and installed it. But, when I restart and boot from the hard drive, the screen become heavily distorted immediately after I leave the grub screen, and I can do nothing but hot reboot manually to windows. I am using a nvidia GT610. Could someone help me with this?

---

### Post by grahammechanical on 2013-09-13
At the Grub boot screen select Recovery Mode>Resume and see if that gets you to a desktop and then open the Additional Drivers Utility and experiment with a different video driver. Did you Try Ubuntu before installing? How did that work? You might want to use the Nouveau open source video driver. It is the same one that runs the Ubuntu live session.

Regards.

---

