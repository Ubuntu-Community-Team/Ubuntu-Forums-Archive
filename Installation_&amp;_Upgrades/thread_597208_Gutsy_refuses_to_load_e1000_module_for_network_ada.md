---
title: "Gutsy refuses to load e1000 module for network adapter"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Saubazi on 2007-10-30
I updated to Gutsy and now modprobe e1000 fails complaining about a bad eeprom checksum. I have now tried to modprobe eeprom_bad_csum_allow=1 option but Gutsy refuses to recognise the option for e1000 module. Now how am I going to get my network adapter up and running again?

---

### Post by Saubazi on 2007-10-31
Once again it seems I have to answer my bit myself, seems to be a problem with Ubuntu coming from Gentoo. Anyway I switched off my integrated adapter from bios - booted up. Rebooted and switched it on again.

---

