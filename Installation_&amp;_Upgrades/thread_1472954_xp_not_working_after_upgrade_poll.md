---
title: "xp not working after upgrade poll"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by vinod_home on 2010-05-04
Hi,

Just trying to analyse why there are so many issues with dual boot after the upgrade.

My story is,  
1. I had only Windows xp on my computer
2. I installed Windows 7 RC on a partition
3. I uninstalled Windows 7 RC around april
4. Removed Windows 7 bootloader using [B]
   [DVD Drive Letter]:\boot\bootsect.exe /nt52
[/B]5. Installed ubuntu 9.10 into a new partition with grub as dual-boot
6. Upgraded to 10.04 and XP was not working using dual boot 

Want to know how many people used Windows 7 bootsect to clean up the bootloader on their machines, maybe that has something to do with why XP is not clean.

TIA

---

### Post by lavinog on 2010-05-04
What is not working?
There was an issue the day of the release where grub was not adding windows entries to the menu, but that should be fixed now...if this is the case, check for any updates.

---

