---
title: "Installation of Ubuntu on Supermicro Workstation"
date: 2017-04-11
forum: Installation &amp; Upgrades
---

### Post by stulli on 2017-04-11
Hey everyone,

I already had a look through old and recent threads, but I did not find anything matching my issue. I want to install Ubuntu 16.04 on one SSD (of two similar SSD), while having a normal HDD set as P0. Bios is set to Legacy mode with the respective SSD set as priority for booting. The two SSD are connected via PCIe. The installation and subsequent booting of Scientific Linux works fine. The Ubuntu installation works fine from USB, but booting ends up with a black screen. I have to crash the system in order to restart the system.

I never had trouble to install Ubuntu so far. Anyways, some specs:

Mainboard X10DAi, BIOS R-2.0a

1x 4TB SATA3 HDD set as P0
2x 512 GB SanDisk X400, M.2
2x GTX 1080Ti

Does anyone have an idea why booting works fine with SL and not with Ubuntu (SL is not an option; I definitely need Ubuntu running)? I already tried to install the boot loader on the HDD while having the system on the SSD, completely install the system on the SSD and completely on the 4TB HDD. Nothing worked so far. 

Maybe someone has an idea. 

Thank you in advance!

---

### Post by mörgæs on 2017-04-12
Hi, welcome to the fora.
Have you tried Buntu 17.04?

---

