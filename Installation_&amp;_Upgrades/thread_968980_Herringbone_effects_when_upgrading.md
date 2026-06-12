---
title: "Herringbone effects when upgrading"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by kentuckylodge on 2008-11-03
I have been trying to upgrade from v.7.04 to the latest, 8.10.  When I get to the page showing install the screen is covered with a herringbone effect. I considered the graphics might not be right but with the older version the graphics are good.  I have also tried to upgrade to 8.04 but get the same results.  Any clues appreciated.

---

### Post by prshah on 2008-11-03
> **kentuckylodge said:**
> I have been trying to upgrade from v.7.04 to the latest, 8.10.  When I get to the page showing install the screen is covered with a herringbone effect. 

From 8.04 onwards, the /etc/X11/xorg.conf file has been marginalised. However, it will not ignore settings that are present in the file. 

One possible reason could be that the DefaultDepth is set to 16 (-bit) in the 7.04 /etc/X11/xorg.conf file. Here's how you can confirm```
cat /var/log/Xorg.0.log | grep -i depth
``` If it shows 16 or lower (24 or 32 is fine), then you should comment out the "DefaultDepth" line in your old xorg.conf, or, better yet, (re)move the file. 

In general, from 8.04 onwards, you do not need a xorg.conf file, and a missing file is automatically re-created with defaults. So, open a terminal (Applications-Accessories-Terminal) and move the old file away; ```
sudo mv /etc/X11/xorg.conf /root
``` then logout, and restart the X server with Ctrl+Alt+BkSpace.

Post back for recovery instructions if you run into problems.

---

