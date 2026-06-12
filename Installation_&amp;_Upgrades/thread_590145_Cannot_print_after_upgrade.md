---
title: "Cannot print after upgrade"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by VictorR on 2007-10-24
After upgrading from 7.04 to 7.10 suddenly found that cannot print anything at all. Everything seems working fine, but if I try, say Print Test Page, the printer icon appears for a moment in the Notification area, and nothing more happens.
I use CUPS and two printers - Brother MFC-210C via USB, and virtual PDF printer. Both does not work now, although they worked fine on Feisty. The MFC210C printer is connected, I can see the memory card in its slot, everything shows ready.

My system: Athlon-XP 2600, 1 GB RAM, nVidia GeForce 4 MX440.; Ubuntu 7.10 with Gnome, Compiz Fusion

Help, please, cannot understand what is wrong.

---

### Post by VictorR on 2007-10-24
Had to reinstall both the printer driver and its CUPS wrapper as described here:
[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html")

After this both physical and virtual PDF printers work fine! :guitar:

---

