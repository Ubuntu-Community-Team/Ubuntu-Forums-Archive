---
title: "Upgraded to Gutsy, and now stuck in Bootloader hell"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by klikko on 2007-10-20
During the upgrade to 7.10, while i was watching the many package updates scroll away (because i have absolutely nothing better to do), i noticed that at least one thing mentioning "grub" was being installed/configured. I myself had LILO at the time, and thought "I hope that wasn't something that'll screw up my bootloader..."

Fast forward to the end of the installation: Gutsy tells me it will reboot, and does so. I'm then presented with the following LILO error:
*EBDA is big. Kernel setup stack overlaps LILO second storage.*
So eventually, finding absolutely nothing helpful about this, i reinstalled LILO with the same result.

I then decided to install GRUB, which seemed to work just fine the first time i booted. However, come the second boot, my system gets stuck in a reboot cycle until i change the boot device.

I reinstalled GRUB, and it seemed to be fine, booting multiple times. I let it alone for the night, and this morning, when i turned it on, it booted just fine. However, when i rebooted... cyclic reboot hell...
I've tried to reinstall GRUB _again_, but now it won't even work a single time.

Any ideas as to what's going on, or what i should do?

---

