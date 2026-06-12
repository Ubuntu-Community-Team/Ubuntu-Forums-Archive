---
title: "Blacklisted Intel Wifi card on AMD mobo."
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by GlasGhost on 2012-06-12
I want to do something [[COLOR="Blue"]similar to this[/COLOR]]("http://web.archive.org/web/20071016063645/http://www.dagarlas.org/stuff/computing/article0001.php") but for a [[COLOR="Blue"]Intel wifi/bluetooth 3.0[/COLOR]]("http://www.intel.com/content/www/us/en/processors/centrino/centrino-wireless-n-1030-brief.html") card that is blacklisted or not whitelisted on my amd mobo bios.

I need help on how to do step 2, I don't know how to write the pci id

Step 1 get current wifi device ID:
I'm 1st gonna boot ubuntu to get the ID with:
```
lspci -nv
```

Step 2 hot plug new card after POST and record its ID and write in the old wifi device ID:

step 3 reboot and install drivers

---

