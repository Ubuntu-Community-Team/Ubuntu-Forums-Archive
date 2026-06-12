---
title: "Hard disk not seen during install, NVIDIA integrated chipset"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by nrdlnd on 2008-06-06
Hi,
I've built a computer with the Jetway NC62K mainboard. It's a very nice Mini ITX board with NVIDIA MCP78S integrated chipset (nvidia 8200) with support for AMD CPU:s. I have managed to log into Hardy with the live cd and I have internet connection with the LAN. The Samsung SATA disk is recognized in the bios but when I try to install Ubuntu don't see the hard disk.

Please howto!

---

### Post by Pumalite on 2008-06-06
Maybe editing your boot line and adding at the end: all_generic_ide will do it.

---

### Post by nrdlnd on 2008-06-07
Thank you very much! I restarted the live cd and put the above line where you said I should and voila the hard disk was found. There is other problems with this chipset though and when I tried to activate the restricted Nvidia driver, X failed to start. I will try Envy though instead.

---

