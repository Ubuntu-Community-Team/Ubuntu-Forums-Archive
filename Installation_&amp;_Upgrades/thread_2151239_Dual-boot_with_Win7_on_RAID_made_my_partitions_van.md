---
title: "Dual-boot with Win7 on RAID made my partitions vanish?"
date: 2013-06-03
forum: Installation &amp; Upgrades
---

### Post by SeaWyrm on 2013-06-03
Hi,
I've been trying to dual boot Windows 7 with Kubuntu on my new laptop. I've got two 750GB hard drives in RAID 1. I installed Windows, then installed Intel RST, then put in my Kubuntu 12.04 Alt disc. It seemed to install fine with RAID enabled and booted after the installation with no problems. However, after rebooting, I'm getting stuck with some sort of grub rescue prompt.
To investigate this problem, I booted from the alt CD and went into rescue mode, only to be told that it couldn't find any boot partitions. It gave me a command prompt, where I tried fdisk -l. Only my Windows system and boot partition showed up, with no sign of the other three I had made.
I've set up multiple dual boot systems before, but never alongside RAID, so I'm guessing this is a RAID-related problem. I've read that people find they need to disable RST before installing Kubuntu, but I had no trouble installing it - at least, not until I rebooted. 
My next step will probably be to try repairing the Windows boot record so I can (hopefully) get back into Windows, then see if disabling RST helps. But in the meantime, can anyone out there shed any light on this?

---

