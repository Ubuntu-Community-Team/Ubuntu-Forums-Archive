---
title: "Problem to bring up any connection with NM"
date: 2008-09-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by emilus on 2008-09-23
Hi,
Last days I have updated my laptop with ubuntu interpid, I know that is Alpha but why not. All works good but I have big problem to connect with any (wired or wireless) connections. Problem is to retrieve network address from DHCP by NM. I can retrieve address manually calling dhclient (with NM disabled). 
Maybe problem is with some old configuration (I tried purge NM and hal) but I dont now what I should reconfigure. 
I will be very grateful If somebody could help me.
This is NM connection log from syslog:

Sep 23 23:18:29 wpilap NetworkManager: <info>  (eth1): device state change: 7 -> 3 
Sep 23 23:18:29 wpilap NetworkManager: <info>  (eth1): deactivating device. 
Sep 23 23:18:29 wpilap NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 19543 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Activation (eth1) starting connection 'easyspot02' 
Sep 23 23:18:29 wpilap NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Sep 23 23:18:29 wpilap NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 0 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Sep 23 23:18:29 wpilap NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Activation (eth1/wireless): connection 'easyspot02' requires no security.  No secrets needed. 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Config: added 'ssid' value 'easyspot02' 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Sep 23 23:18:29 wpilap NetworkManager: <info>  Config: set interface ap_scan to 1 
Sep 23 23:18:29 wpilap NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Sep 23 23:18:30 wpilap NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 4 
Sep 23 23:18:30 wpilap NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Sep 23 23:18:30 wpilap NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'easyspot02'. 
Sep 23 23:18:30 wpilap NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep 23 23:18:30 wpilap NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Sep 23 23:18:30 wpilap NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Sep 23 23:18:30 wpilap NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Sep 23 23:18:30 wpilap dhclient: Internet Systems Consortium DHCP Client V3.1.1
Sep 23 23:18:30 wpilap dhclient: Copyright 2004-2008 Internet Systems Consortium.
Sep 23 23:18:30 wpilap dhclient: All rights reserved.
Sep 23 23:18:30 wpilap dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Sep 23 23:18:30 wpilap dhclient: 
Sep 23 23:18:30 wpilap NetworkManager: <info>  dhclient started with pid 19953 
Sep 23 23:18:30 wpilap NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Sep 23 23:18:30 wpilap dhclient: Listening on LPF/eth1/00:14:a5:73:3f:90
Sep 23 23:18:30 wpilap dhclient: Sending on   LPF/eth1/00:14:a5:73:3f:90
Sep 23 23:18:30 wpilap dhclient: Sending on   Socket/fallback
Sep 23 23:18:32 wpilap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Sep 23 23:18:32 wpilap dhclient: DHCPOFFER of 10.0.0.6 from 10.0.0.1
Sep 23 23:18:32 wpilap dhclient: DHCPREQUEST of 10.0.0.6 on eth1 to 255.255.255.255 port 67
Sep 23 23:18:32 wpilap dhclient: DHCPACK of 10.0.0.6 from 10.0.0.1
Sep 23 23:18:32 wpilap dhclient: bound to 10.0.0.6 -- renewal in 427 seconds.
Sep 23 23:18:34 wpilap NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 3 
Sep 23 23:18:35 wpilap NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Sep 23 23:18:35 wpilap NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Sep 23 23:19:15 wpilap NetworkManager: <info>  Device 'eth1' DHCP transaction took too long (>45s), stopping it. 
Sep 23 23:19:15 wpilap NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 19953 
Sep 23 23:19:15 wpilap NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Sep 23 23:19:15 wpilap NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Sep 23 23:19:15 wpilap NetworkManager: <info>  (eth1): device state change: 7 -> 9 
Sep 23 23:19:15 wpilap NetworkManager: <info>  Activation (eth1) failed for access point (easyspot02) 
Sep 23 23:19:15 wpilap NetworkManager: <info>  Marking connection 'easyspot02' invalid. 
Sep 23 23:19:15 wpilap NetworkManager: <info>  Activation (eth1) failed. 
Sep 23 23:19:15 wpilap NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Sep 23 23:19:15 wpilap NetworkManager: <info>  (eth1): device state change: 9 -> 3 
Sep 23 23:19:15 wpilap NetworkManager: <info>  (eth1): deactivating device. 

It is strange because in this log you can find that dhclient get address from DHCP server but few second later NM say that:

Device 'eth1' DHCP transaction took too long (>45s), stopping it.

---

### Post by Iowan on 2008-09-23
> **emilus said:**
> Hi,
Last days I have updated my laptop with ubuntu interpid, I know that is Alpha but why not.For that reason, you may wish to move this to the Development area.

---

### Post by Rocket2DMn on 2008-09-23
Moved to Intrepid Ibex Testing and Discussion forum - you might get better help here.  However, when using development releases, you should expect breakage, so it is not recommended for most users unless you like filing bug reports and breaking things.

---

### Post by Nullack on 2008-09-23
Theres a number of existing bugs on NM 0.7 in launchpad.

Please refer to the link in my sig about how you could possibly contribute to Intrepid.

---

### Post by emilus on 2008-09-24
I seams that I have found problem.
Before I have updated my system to intrepid I had been updated with NM beta from hardy repository because of OpenVPN routing problem. After my update to intrepid I forgot to change NM repository from hardy to intrepid. 
Since I have changed NM repository to the right one everything works fine.

E.

---

