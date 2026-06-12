---
title: "How to install broadcom wireless"
date: 2012-04-08
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2012-04-08
I just installed kubuntu oneiric.  I now want to get my wireless working, and need to install the broadcom drivers/firmware.  Under ubuntu I just search for b43 in synaptic and installed the packages.  Under kubuntu I searched in Muon for b43, but nothing came up.  I have wired ethernet up and running.  I have a Breadcom 4318, which takes the b43 drivers under ubuntu.

Any help appreciated!!
Ralph

---

### Post by 2F4U on 2012-04-08
I don't use Kubuntu, but you should be able to open a terminal and execute

sudo apt-cache search b43

---

### Post by Ralph L on 2012-04-08
My bad.  I must have done the search wrong in Muon Package Manager.  When I search for broadcom I found b43-fwcutter, installed it, went to the lan/wan icon in the tray, selected my wireless network (took a minute to find the network), and everything worked.  Later I went back to muon and searched again for b43-fwcutter and it came right up.

Thanks for the help.

Ralph

---

