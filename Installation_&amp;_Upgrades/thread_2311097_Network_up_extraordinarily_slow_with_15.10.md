---
title: "Network up extraordinarily slow with 15.10"
date: 2016-01-24
forum: Installation &amp; Upgrades
---

### Post by y-tech on 2016-01-24
I've recently upgraded from 14.04 to 15.10. After the upgrade, the nework takes a very long time to get established, on the average of 5 minutes after boot. I've timed this in an rc.local script waiting for getent to contact the server (the domain server is in-house and is also the DNS server and DHCP server for the LAN). It is also taking a very long time to see other hosts on the LAN. The NFS startup fails because it cannot resolve the NSF server hostname. I cannot ssh from an external host to the Ubuntu host for 5 minutes or so after boot. No other hosts on the LAN have this problem and I did not have this problem with 14.04.

Does anyone have any insight? Is there a place to post "bugs" for Ubuntu?

---

