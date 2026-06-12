---
title: "Both GRUB and LILO hang on first re-boot"
date: 2005-01-31
forum: Installation &amp; Upgrades
---

### Post by casito on 2005-01-31
The installation seemed to go off without a hitch until the first re-boot. GRUB locks up between 1.5 and 2.  I then tried LILO to no avail. It  got as far as printing the 'L' on the screen, then spat out scores of the number 99.  I read somewhere that an old BIOS may cause this, so I re-flashed both the motherboard and the ata card. This did not help.  

Epox 8KHA+ Mainboard
Promise FastTrak TX2000 ATA controller
Two WD800BB drives on both master channels of the controller

Unfortunatly, Ubuntu ignores the RAID capabilities of the ATA card, so I am grudgingly forced to use software RAID.   The root file system is being mounted to a non-RAID-ed partition of one of the drives.

Any help would be greatly appreciated.

---

