---
title: "Lucid on Samsung NB30 - no wireless"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by scotty64 on 2010-04-30
I installed Lucid on my Samsung NB30 netbook. The problem is the wireless. 
I managed to get it switched on by using the "easy-slow-down-manager" [http://code.google.com/p/easy-slow-down-manager/](http://code.google.com/p/easy-slow-down-manager/)
It loads the r8192_pci module, but it does not work.
listing the network hardware comes up with: *-network DISABLED
I tried to install the windows driver with ndiswrapper.
The problem here is that although I created a blacklist-rtwireless.conf file, the system stubbornly loads r8192_pci and wireless does not work.

---

### Post by scotty64 on 2010-05-01
The problem is solved:
Although the kernel module does not work, I managed to get it properly blacklisted. I just forgot to put "blacklist" before the module name :lolflag:
I can use the wireless with ndiswrapper now.

---

