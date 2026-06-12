---
title: "DHCP3 server fails start after upgrade to 11.04"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by funky_D on 2011-05-05
i need some help.. i have my dhcp.conf still intact, but no dhcp daemon stars when i do /etc/init.d/dhcp3-server start

sudo: /etc/init.d/dhcp3-server: command not found

i regret so much to have done the upgrade!!

thanks for helping..

---

### Post by srwafu on 2011-05-09
Im having the same problem, I found this note in the bug tracker;


                 dhcp3 is no longer in Natty archive, it's been replaced by a transitional package to isc-dhcp (v4), marking Natty task invalid for dhcp3.  ** Changed in: dhcp3 (Ubuntu Natty)        Status: Triaged => Invalid  

Not really very helpful, but at least I know its not something I did to screw up the dhcp3-server, its a development issue.  Trying to find a work around for LTSP though :/

---

### Post by zuffi on 2011-05-09
The upgrader copied your config into the new package at ```
/etc/dhcp/
``` So just check if the configs are still valid for your enviroment and start your server with the new init-script ```
/etc/init.d/isc-dhcp-server start
```You should be golden after that, did it for my failover dhcp/ddns-servers with no further troubles. If your dhcp3-folder contains any modified files, it will not be removed automatically by the updater.

---

### Post by SHlTHEADJOE on 2011-05-17
Thanks you very much.  That fixed it!!!! 
sudo /etc/init.d/isc-dhcp-server start

---

