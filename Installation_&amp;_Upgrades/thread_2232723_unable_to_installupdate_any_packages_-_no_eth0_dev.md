---
title: "unable to install/update any packages - no eth0 device found after netboot install"
date: 2014-07-03
forum: Installation &amp; Upgrades
---

### Post by SponezillA on 2014-07-03
Hello All,

Here's what I'm looking at. After a netboot install, via netboot files that were hosted on my 12.04 workstation thru a router to a 2004 Dell laptop, I had no access to networking AFTER the system was successfully installed. I set up my user accounts and can log in as root. I found this problem when I realized I do not have the X Window System. (I think it was because I selected as bare as I could so the system would install). I concluded that the system lacks the appropriate drivers and needed software to detect any network settings.

ifconfig shows no indication of eth0, only loopback

lspci does show the ethernet controller on its output list

I can't ping my newtork router

route -n is blank

tail /var/log/syslog shows:

eth0: No such device


So how would I get the right driver to get this machine to see my ethernet driver? Could I reload the netboot files and update/repair that way?

---

### Post by floyderoberts3 on 2014-08-12
Very similar problem (same problem?) upgrade to 14.04 network install of packages during install works great on restart Ethernet nor WiFi is seen by system. Ethernet cable works in other system side by side but Machine does not see installed internet OR WiFi

---

