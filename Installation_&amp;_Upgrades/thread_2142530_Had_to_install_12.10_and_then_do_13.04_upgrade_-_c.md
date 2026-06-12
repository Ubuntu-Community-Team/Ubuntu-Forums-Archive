---
title: "Had to install 12.10 and then do 13.04 upgrade - couldn't install 13.04 directly."
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by arrowcatcher on 2013-05-06
Have HP H8-1420t i7 "ENVY" desktop.  Installed a second SATA drive for Ubuntu. 
 
Version 13.04, whether 32 or 64, would not install properly as this distribution supports neither the Atheros AR8161 NIC nor the Ralink RT5390R WiFi in this off-the-shelf HP machine.  13.04 does install directly but was a total zombie without any Internet support.

I found that versions 12.04 LTS-64 and 12.10 both 32/64 would install with Internet support using the WiFi adapter but not the NIC.  After a number of successive reinstallations I settled on version 12.10-64 and then simply upgraded it to 13.04-64, which works fine, but only with the WiFi.  Hopefully a successive kernel will support the Atheros AR8161.

Dunno why the successor 13.04 version lost my essential WiFi support.  It makes 13.04 uninstallable on a line of HP desktops and maybe more without doing this trick of first installing 12.10 and then doing an upgrade, a two step process.

---

