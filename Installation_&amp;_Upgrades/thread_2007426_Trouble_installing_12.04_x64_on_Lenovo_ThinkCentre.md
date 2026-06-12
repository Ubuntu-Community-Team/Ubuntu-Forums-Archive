---
title: "Trouble installing 12.04 x64 on Lenovo ThinkCentre M81 7518D4U"
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by paultrotter88 on 2012-06-20
I've attempted to install 12.04 64-bit on my ThinkCentre M81 7518D4U a couple of times now. I can get through the installation just fine, but when I get to the point where it asks me to restart so that I can use the installed system, the disk I've installed to won't boot up. My system then tries to network boot, and then nothing happens.

In the BIOS, I've made sure that my hard disk is in the boot order right after the CD/DVD-ROM.

Is there another setting in the BIOS that I'm missing? The BIOS is relatively new. Last updated 01/10/2012.

---

### Post by paultrotter88 on 2012-06-20
Figured it out. I had to disable UEFI in my system's "BIOS". Switched it to "Legacy" and it's booting fine now.

---

