---
title: "Unable to restart via case switch"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by wongjos1 on 2008-10-16
My system:

ATI HD 3850 AGP video card
MSI K8N Neo2 Mobo
AMD Athlon X2 4200+
2GB ram.
4x IDE devices (2xHD, 2xcd-rom)

I'm trying to install Ubuntu. I've downloaded the AMD64 edition of Ubuntu, installed it following the normal install procedures. The system boots into a stable desktop using the vesa drivers. However, once I try to enable the ATI drivers, the system crashes. This isn't your normal crash. I cannot switch consoles, soft reboot (ctrl+alt+delete) OR hard reboot, the reboot button on my case doesn't work. Anyone have any theories on how this is remotely possible and a solution that allows me to use the ATI drivers?

---

### Post by cariboo on 2008-10-16
The power and reset switches are momentary contact switches, all the do is short two pins. I have run into this problem in Windows, pulling the power cord and plugging it back in again usually solves the problem. As for your If you are trying to install 8.10 new ATI drivers just came out yesterday and are already in the repositories.

Jim

---

### Post by wongjos1 on 2008-10-16
I know that the switches are simply contact switches, but that doesn't explain how Ubuntu can prevent the motherboard from rebooting. I've tested the switches when I'm running from a live CD, in windows and when I'm in the bios, the switches are working. I was trying to install Ubuntu 8.04, as 8.10 is not a stable release yet. Is it possible that the ATI drivers that are in the 8.04 repository are not new enought to support the HD 3850?

---

