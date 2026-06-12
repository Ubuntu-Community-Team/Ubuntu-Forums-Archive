---
title: "Install Hangs On USB/SCSI Devices"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by paxster on 2011-11-08
I just got a Dell XPS 8300 desktop with Intel Core i7-2600 processor, Nvidia Geforce GT530, 2TB Serial ATA 2 Hard Drive 7200 RPM, 8GB memory. There is also a card reader. During the boot process of the install it will hand when it is processing the USB and SCSI devices. I passed nousb but it hangs when probing the cd drive and hard drive, calling them scsi devices.

Any thoughts about how to fix this. I'm trying to install 64bit 11.10

---

### Post by paxster on 2011-11-09
It also has 2 USB 3.0 ports that may also be causing problems.

---

### Post by p_motch on 2011-11-12
I'm having the same issue myself. If you end up figuring out the problem, please post an update.

---

### Post by paxster on 2011-11-12
I was able to get it to boot into the installer using acpi=off.
After I installed it, it was able to boot without that command line option.

When the screen come up with the options to try without installing or install, select which one you want and then press F6. Select acpi=off (an x should appear next to it). Then press esc and then enter to boot.

---

