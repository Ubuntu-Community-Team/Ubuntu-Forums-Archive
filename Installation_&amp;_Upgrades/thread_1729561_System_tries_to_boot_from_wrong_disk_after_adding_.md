---
title: "System tries to boot from wrong disk after adding SSD"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by gwi on 2011-04-15
Hello all,

Not sure if this is an Ubuntu problem or a hardware (Asus) problem.

I added an SSD (Intel SSD 320 80GB) to my system (motherboard is an Asus M2N32 SLI). I reinstalled Ubuntu 10.10 64 bit, with partitions for /, /boot, /usr on the SSD, and /home on the harddisk. Harddisk and SSD are SATA devices. The old installation is still on the harddisk.

When I boot my system, I get the Grub2 menu from the harddisk, not from the SSD. I have to press F8 to get to the boot device menu, and select the SSD.

After removing the Grub2 installation from the harddisk, the system no longer shows that menu, but it also does not show the Grub2 menu from the SSD. I only get a black screen with a flashing cursor, so I still have to press F8 to manually select the SSD. After manual selection I get the correct Grub2 menu, and Ubuntu boots normally.

I even swapped the SATA connections, but that didn't solve the problem.
The boot partition on the SSD (primary partition 1) is marked active. The former boot partition on the harddisk (primary partition 1) is marked inactive.

How can I get the system to boot automatically from the SSD instead of trying to boot from the harddisk?

Well, I can answer my own question :oops: In the BIOS menu's I found an option to set the SATA disk order. Apparently this order is not determined by the SATA connector a disk is attached to (as swapping the connections showed), but by a more "intelligent" mechanism.

---

