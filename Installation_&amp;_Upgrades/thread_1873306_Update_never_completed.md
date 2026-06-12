---
title: "Update never completed"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by bkleine on 2011-11-01
Hi,

I have upgraded from 11.04 to 11.10 and almost everything went well. The problem was due to a parallel texlive2011 installation but that I could manage well. 

However, I never could run a Restart: first of all in the new kde-plasma the button for shutdown is now missing! this is not well done. 

Furthermore any shutdown from CTRL-ALT-F1 root failed due to **sipwitch** not shuting down. Since I never used VOIP, I managed to remove the entire package using dpkg. 

The most grave error is the fact that during shutdown the /var/run/dbus/Pid file is not removed. this blocks normal start. I had already earlier complained that on my computer umount does no longer happen if not forced. This is messy. 

Last of all, the directory /run/network was never created which blocked the use of an unmanaged ethernet card.

Hopefully this helps someone else. I have spent several hours now to get a working desktop.

Bernhard

---

### Post by bkleine on 2011-11-01
Hi, 

this is the real blocker! as long as I remove manually this file before shutting down I get a proper boot and startup of any desktop I want. However, without this manual removal, the booting is stopped due to the modem-manager not being able to connect to the proper socket. 

Is there any remedy?

Bernhard

---

