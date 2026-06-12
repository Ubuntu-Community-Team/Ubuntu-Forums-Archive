---
title: "Grub Error 17 - cant find solution."
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by csanchezotero on 2005-04-14
I have done searches on this and can't find a solution.

Windows kept BSODing and I decided to install Kubuntu from scratch after backing up all my files on windows.  Windows was setup as SATA raid(0).

I no longer have windows installed as i removed the partitions during Kubuntu install and setup fresh linux paritions.  

Once the initial setup was complete and setup wanted to reboot, upon rebooting I get a grub error 17.  I have done some searches and I am unable to find a solution to this problem.

Does any one know of a way to fix this?

---

### Post by alastair on 2005-04-14
If windows was using RAID with SATA, is this a SATA RAID option in the BIOS? Linux often does NOT have a driver for this (but windows will) because it is s/w RAID. Worth checking your BIOS.

---

