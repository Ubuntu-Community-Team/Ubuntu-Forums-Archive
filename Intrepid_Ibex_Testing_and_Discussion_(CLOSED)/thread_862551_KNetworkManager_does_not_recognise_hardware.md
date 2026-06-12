---
title: "KNetworkManager does not recognise hardware"
date: 2008-07-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MoridinBG on 2008-07-17
Kubuntu Alpha here

After a bunch of updates (167 to be more precise) KNetworkManager states that "there is no network hardware". iw/ifconfig enlist both the LAN and WLAN and I am abble to connect via pon dsl-provider (PPPoE here). Wireless is disabled in KNetworkManager and I can't enable it.

The LAN is Broadcomm Gigabit Extreme and the WLAN is Intel 2200BG

---

### Post by psyke83 on 2008-07-17
> **MoridinBG said:**
> Kubuntu Alpha here

After a bunch of updates (167 to be more precise) KNetworkManager states that "there is no network hardware". iw/ifconfig enlist both the LAN and WLAN and I am abble to connect via pon dsl-provider (PPPoE here). Wireless is disabled in KNetworkManager and I can't enable it.

The LAN is Broadcomm Gigabit Extreme and the WLAN is Intel 2200BG

Did you do a fresh install from the CD? If so, install the package "linux-restricted-modules-common" and reboot.

---

### Post by caryb on 2008-07-17
Sorry but that does not work! I have a wireless & ethernet connection & have had no entries in my knetworkmanger since my rebuild at alpha 1 here is a dump of my attempt to install linux-restricted-modules-common

root@stinkpad:~# apt-get install linux-restricted-modules-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-restricted-modules-common is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.26-3-generic linux-headers-2.6.26-3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@stinkpad:~#
 

Cary

---

### Post by Vorian on 2008-07-17
run (alt+F2)
```
knetworkmanager
```

---

