---
title: "what if the network is down after the first reboot?"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by oik on 2005-10-22
OK, so this is a network install. The install process downloads and installs a whole bunch of stuff, then reboots. After the reboot, it tries to download a load more stuff.

In my case (running on VMWare player), for some reason ubuntu got configured with the wrong default route. (Does VMWare install it's own DHCP server or something?). After the reboot, it failed to do the downloads and left me at a console login.

I fixed the networking, and rebooted (several times before I got it all sorted). However, now, it doesn't even try to finish the install, and just leaves me at a console login.

So, my question is, what command do I need to run to finish the installation?

Regards,

Oik

---

