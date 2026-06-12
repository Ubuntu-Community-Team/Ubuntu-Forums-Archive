---
title: "X broken after upgrading to 10.10 alpha"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by adityavpratap on 2010-08-22
Hi,
I upgraded to Ubuntu 10.10 from 10.04 today. However when I rebooted after the upgrade, I was a presented with the text mode instead of the regular graphical mode.
I tried to do sudo dpkg-reconfigure xserver-xorg, but still I couldn't log into graphical mode.
Then I copied the xorg.conf.failsafe to /etc/Xorg/xorg.conf and did a startx. This time I was able to log into GNOME, but the resolution was restricted to 1024 x 768 instead of the usual resolution for my Acer Aspire 5738z laptop which has an Intel GMA 4500 M graphics card.
Any suggestions?

---

