---
title: "Disk boot failure after fresh install"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2010-10-16
Hi,
After buying a new PC, I decided to "reorganize" my former PC as follows:
[LIST=1]
[*]Initially it has been a dual (SATA) disk dual boot PC- one disk for each OS, while XP was fully installed on a **single** NTFS partition.
[*]Using Gparted I shrunk the XP partition, and created some Linux partitions. I've verified that the XP partition (sda1) is bootable.
[*]Afterwards, I removed the other (former Linux) disk from the computer. While doing so, I had to temporarily disconnect cables from both drives.
[*]Finally, I  fresh installed Mint 9 (Ubuntu 10.04 derivative), on my pre-prepared Linux partitions. Installation completed flawlessly, and during the install, I've noticed that GRUB2 has been installed on sda.
[*]Rebooted and got "Disk boot failure" error.
[/LIST]

I've checked the BIOS and noticed that the (single) drive was not recognized. 
I manually tested from the BIOS and located the drive as IDE3.
Saving the new configuration (F10) and rebooting- the HD gain is **not** identified (the CMOS battery is fine- keeps time).

Booting a live CD I can see and access all above partitions.

Please advise how to bring my PC back to life..

Thanks!

---

### Post by wilee-nilee on 2010-10-16
Post the bootscript in my signature in code tags.

---

### Post by mibadt on 2010-10-16
Solved by moving the sata cable to different motherboard connectors (trial & error) till it has been recognized by BIOS.

---

