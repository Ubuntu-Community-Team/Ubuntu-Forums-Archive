---
title: "No Internet/Synaptic but can ping &amp; DNS"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by Shakeysteve on 2008-09-25
When I run a live cd or install 8.04 or 7.10 I have no internet connection or synaptic, yet ping & DNS work fine. 6.06 works fine right from install.
What has changed in later Ubuntu versions? Is there a new firewall or something?

Thanks for any help,
Steve.

---

### Post by iaculallad on 2008-09-25
Try changing your NameServer (try not to use your router's IP address). Select "Network" from the System->Administration menu and from there click on the "DNS" tab, you will see your routers IP address (i.e: 192.168.1.1) you need to remove this and replace it with your ISP's DNS entries.

---

