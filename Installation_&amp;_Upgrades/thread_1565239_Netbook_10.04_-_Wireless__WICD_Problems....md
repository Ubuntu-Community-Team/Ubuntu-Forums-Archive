---
title: "Netbook 10.04 - Wireless / WICD Problems..."
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by algomedic on 2010-08-31
I've installed Ubuntu Netbook 10.04 and the wireless does not work.  I've read to install WICD and use that instead.  Problem is, it tells me to uninstall "Network Manager" which I did through:

sudo apt-get remove NetworkManager

When I go to install WICD, it states:

Error: Conflicts with the installed package 'network-manager'

Any ideas on how to fully uninstall Network Manager or a fix to why wireless and wired does not work with Ubuntu Netbook 10.04...

Thank in advance.

---

### Post by zvacet on 2010-08-31
Find network-manager package in synaptic and uninstall it.After that install wicd.

---

### Post by algomedic on 2010-08-31
wow, okay that worked in uninstalling network manager and installing WICD

I now have wired access, I still cannot connect to my wireless, it is not showing up

Any ideas???

Thanks for your help

---

### Post by zvacet on 2010-09-01
In wicd under hidden networks try to establish wireless.

---

