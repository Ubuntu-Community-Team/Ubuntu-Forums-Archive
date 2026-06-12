---
title: "Ubuntu 12.04 won't get installed in UEFI pc"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by Harri_Hyokyvaara on 2014-04-01
I have following set up:
- PC: Advantech ark-2120 in BIOS CSM Support is set to Auto
- Two displays one in HDMI and other in VGA output
- Ubuntu 12.04.4 USB installation media
- Ubuntu 13.10 USB installation media

With Ubuntu 12.04:
- Installation goes nicely
- After rebooting I get GNU GRUB start up menu
- Select: Ubuntu, with Linux 3.11.0-15-generic
--> both displays stays blank

With Ubuntu 13.10
- Installation goes nicely and everything works ok after installation. 

Problem is that I need to use 12.04 version! so only thing I get with 13.10 is confirmation that there is some ubuntu version which works in ARK-2120 PC. And as a side note 12.04 works correctly in ARK-3360 which for my understanding doesn't have UEFI support

---

### Post by Kris_Spencer on 2014-04-02
I would disable Secure Boot to rule it out. I'm not sure if 12.04 is compatible or not.

---

