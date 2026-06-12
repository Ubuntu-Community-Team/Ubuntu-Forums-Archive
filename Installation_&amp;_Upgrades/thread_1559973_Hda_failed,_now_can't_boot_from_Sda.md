---
title: "Hda failed, now can't boot from Sda"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by eragot on 2010-08-24
Hi,
Don't ask why, but I had Grub running off of Hda, an old 20gb drive that had an install of 9.10 on it, but was never used. This drive has died.

so, my problem:
hda - grub
hdb - data
sdc - 10.4.1 / XP
sdd - clone of sdc, 9.10 

in the above config, everything works - boot to sdc5 from grub and all is well.

then I disconnected hda and hdb, installed another version of 10.4 on sdc (now sda) in order to get Grub working properly. Grub sees Sda5 (the 10.4.1 installation) and starts the boot process.

Boot hangs on a udev error.

I don't know how to fix it.

I reinstalled hda and hdb and all is well again.

I want to get the PATA drives out and just use the SATA drives.

Thanks.

---

