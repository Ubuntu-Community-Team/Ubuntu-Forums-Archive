---
title: "VMWare Server Upgrade and Custom Virtual Network"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by veloce on 2007-05-16
Just a warning to those upgrading their VMWare Server with the latest update (1.0.3).  If you have customised your virtual network settings they will be lost in the upgrade.

I had to 
[LIST=1]
[*]re-run vmware-config-network.pl to customise the virtual networks
[*]edit net-services.sh to disable the dhcp server.
[/LIST]

---

