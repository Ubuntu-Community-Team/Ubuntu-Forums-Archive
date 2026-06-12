---
title: "Installed 6.06 on DL380 G2"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by hdixon on 2008-01-16
FWIW - 6.06 Server worked for me on this box. Changed the boot order to the Array first, hit F6 on the install screen and added apic=off and apm=off and everything seemed to go ok. I made sure to select the free space for the partitioning so the System partition for the utilities stayed put. Reboot went fine and I was able to login.

I may try to see if the same goes for Ubuntu 7. If so I'll update.


Update: Actually those options were acpi=off apm=off

---

