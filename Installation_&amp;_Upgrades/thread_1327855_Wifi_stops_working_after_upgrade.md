---
title: "Wifi stops working after upgrade"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by awacs on 2009-11-15
(updated to Lucid 9.10 with do-release-upgrade) my (orinoco chip) wifi card stopped working; link light blinks continuously, messages in syslog:

Nov 15 17:50:17 yankel-laptop wpa_supplicant[1136]: CTRL-EVENT-SCAN-RESULTS 
Nov 15 17:51:14 yankel-laptop kernel: [ 1087.600148] eth1: New link status: Association Failed (0006)
Nov 15 17:51:14 yankel-laptop kernel: [ 1087.613001] eth1: New link status: Disconnected (0002)
Nov 15 17:51:14 yankel-laptop wpa_supplicant[1136]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 15 17:51:16 yankel-laptop kernel: [ 1089.645354] eth1: New link status: Connected (0001)
Nov 15 17:51:16 yankel-laptop wpa_supplicant[1136]: No network configuration found for the current AP
Nov 15 17:51:16 yankel-laptop kernel: [ 1089.678451] eth1: New link status: Disconnected (0002)
Nov 15 17:51:16 yankel-laptop wpa_supplicant[1136]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 15 17:51:44 yankel-laptop avahi-daemon[700]: Interface eth1.IPv4 no longer relevant for mDNS.

Worked flawlessly in several prior releases, Reverting to 8.04.3 gets it going again. What gives?

---

### Post by awacs on 2009-11-16
Bump, he said hopefully.

---

