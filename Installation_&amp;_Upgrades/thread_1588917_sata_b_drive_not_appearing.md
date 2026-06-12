---
title: "sata b drive not appearing"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by ratcat on 2010-10-05
Install of 10.4  64 bit not showing choice of sata drives on install. W 7 on sata a drive, SUSE 11 on sata b drive. Need to load Ubuntu 10.4 on drive b, but not given choice of drives on the install. Only "clear drive" listed on the install window. 
This is not the case on 32 bit, a graph with drives listed. W7 a runs Adobe CS5, the Ubuntu 10.4 has excellent font, type display on the live cd.
Thanks

---

### Post by dabl on 2010-10-05
In BIOS, set the SATA mode to "Legacy IDE" or "IDE" or whatever is NOT AHCI.  You can set it back to AHCI mode after you have finished installation.

---

