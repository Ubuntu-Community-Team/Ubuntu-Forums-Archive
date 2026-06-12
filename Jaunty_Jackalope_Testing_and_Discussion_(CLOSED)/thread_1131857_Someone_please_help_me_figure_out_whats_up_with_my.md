---
title: "Someone please help me figure out whats up with my wifi card.."
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by spotdog14 on 2009-04-21
Hello, I have posted here a few times about my Dell 1515 wifi card not working correctly, and also problems with the gnome-keyring-daemon not working as well. For a while it was fixed but most recent round of updates seems to have broken it again. 

Here is the last part of the output from my syslog.

```

Apr 21 08:54:44 SXPS13 NetworkManager: <info>  wlan0: link timed out. 
Apr 21 08:54:44 SXPS13 kernel: [  275.144547] wlan0: authenticate with AP 00:19:e2:ec:bc:31
Apr 21 08:54:44 SXPS13 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 21 08:54:44 SXPS13 kernel: [  275.153037] wlan0: authenticate with AP 00:19:e2:ec:bc:31
Apr 21 08:54:44 SXPS13 kernel: [  275.352042] wlan0: authenticate with AP 00:19:e2:ec:bc:31
Apr 21 08:54:44 SXPS13 kernel: [  275.556025] wlan0: authenticate with AP 00:19:e2:ec:bc:31
Apr 21 08:54:44 SXPS13 kernel: [  275.752043] wlan0: authentication with AP 00:19:e2:ec:bc:31 timed out
Apr 21 08:54:54 SXPS13 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Apr 21 08:54:54 SXPS13 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 21 08:54:57 SXPS13 kernel: [  288.172509] wlan0: authenticate with AP 00:19:e2:ec:bc:31
Apr 21 08:54:57 SXPS13 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 21 08:54:57 SXPS13 kernel: [  288.183331] wlan0: authenticate with AP 00:19:e2:ec:bc:31
Apr 21 08:54:57 SXPS13 kernel: [  288.380050] wlan0: authenticate with AP 00:19:e2:ec:bc:31
Apr 21 08:54:57 SXPS13 kernel: [  288.580048] wlan0: authenticate with AP 00:19:e2:ec:bc:31
Apr 21 08:54:57 SXPS13 kernel: [  288.780046] wlan0: authentication with AP 00:19:e2:ec:bc:31 timed out
Apr 21 08:55:07 SXPS13 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Apr 21 08:55:07 SXPS13 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  wlan0: link timed out. 
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 21 08:55:10 SXPS13 kernel: [  301.207793] wlan0: direct probe to AP 00:19:e2:ec:bc:31 try 1
Apr 21 08:55:10 SXPS13 kernel: [  301.210140] wlan0 direct probe responded
Apr 21 08:55:10 SXPS13 kernel: [  301.210144] wlan0: authenticate with AP 00:19:e2:ec:bc:31
Apr 21 08:55:10 SXPS13 kernel: [  301.212856] wlan0: authenticated
Apr 21 08:55:10 SXPS13 kernel: [  301.212859] wlan0: associate with AP 00:19:e2:ec:bc:31
Apr 21 08:55:10 SXPS13 kernel: [  301.215752] wlan0: RX AssocResp from 00:19:e2:ec:bc:31 (capab=0x431 status=0 aid=20)
Apr 21 08:55:10 SXPS13 kernel: [  301.215754] wlan0: associated
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 21 08:55:10 SXPS13 kernel: [  301.227788] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KC'. 
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  dhclient started with pid 4038 
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 21 08:55:10 SXPS13 dhclient: Internet Systems Consortium DHCP Client V3.1.1
Apr 21 08:55:10 SXPS13 dhclient: Copyright 2004-2008 Internet Systems Consortium.
Apr 21 08:55:10 SXPS13 dhclient: All rights reserved.
Apr 21 08:55:10 SXPS13 dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 21 08:55:10 SXPS13 dhclient: 
Apr 21 08:55:10 SXPS13 dhclient: wmaster0: unknown hardware address type 801
Apr 21 08:55:10 SXPS13 NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
Apr 21 08:55:10 SXPS13 dhclient: wmaster0: unknown hardware address type 801
Apr 21 08:55:10 SXPS13 dhclient: Listening on LPF/wlan0/00:22:5f:6f:bd:6a
Apr 21 08:55:10 SXPS13 dhclient: Sending on   LPF/wlan0/00:22:5f:6f:bd:6a
Apr 21 08:55:10 SXPS13 dhclient: Sending on   Socket/fallback
Apr 21 08:55:10 SXPS13 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 21 08:55:12 SXPS13 avahi-daemon[3159]: Registering new address record for fe80::222:5fff:fe6f:bd6a on wlan0.*.
Apr 21 08:55:18 SXPS13 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 21 08:55:18 SXPS13 dhclient: DHCPOFFER of 192.168.11.19 from 192.168.11.253
Apr 21 08:55:18 SXPS13 dhclient: DHCPREQUEST of 192.168.11.19 on wlan0 to 255.255.255.255 port 67
Apr 21 08:55:18 SXPS13 dhclient: DHCPACK of 192.168.11.19 from 192.168.11.253
Apr 21 08:55:18 SXPS13 NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Apr 21 08:55:18 SXPS13 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 21 08:55:18 SXPS13 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Apr 21 08:55:18 SXPS13 NetworkManager: <info>    address 192.168.11.19 
Apr 21 08:55:18 SXPS13 NetworkManager: <info>    prefix 24 (255.255.255.0) 
Apr 21 08:55:18 SXPS13 NetworkManager: <info>    gateway 192.168.11.253 
Apr 21 08:55:18 SXPS13 NetworkManager: <info>    nameserver '192.168.1.5' 
Apr 21 08:55:18 SXPS13 NetworkManager: <info>    nameserver '4.2.2.2' 
Apr 21 08:55:18 SXPS13 NetworkManager: <info>    domain name 'NetScreen-NS5GT-WLAN' 
Apr 21 08:55:18 SXPS13 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 21 08:55:18 SXPS13 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Apr 21 08:55:18 SXPS13 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Apr 21 08:55:18 SXPS13 dhclient: bound to 192.168.11.19 -- renewal in 2147483648 seconds.
Apr 21 08:55:18 SXPS13 avahi-daemon[3159]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.11.19.
Apr 21 08:55:18 SXPS13 avahi-daemon[3159]: New relevant interface wlan0.IPv4 for mDNS.
Apr 21 08:55:18 SXPS13 avahi-daemon[3159]: Registering new address record for 192.168.11.19 on wlan0.IPv4.
Apr 21 08:55:19 SXPS13 NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Apr 21 08:55:19 SXPS13 NetworkManager: <info>  Policy set 'Auto KC' (wlan0) as default for routing and DNS. 
Apr 21 08:55:19 SXPS13 NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Apr 21 08:55:19 SXPS13 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 21 08:55:21 SXPS13 kernel: [  312.145056] wlan0: no IPv6 routers present
Apr 21 08:55:21 SXPS13 ntpdate[4116]: adjust time server 91.189.94.4 offset -0.211919 sec
Apr 21 08:56:45 SXPS13 NetworkManager: <debug> [1240318605.002563] periodic_update(): Roamed from BSSID 00:19:E2:EC:BC:31 (KC) to (none) ((none)) 
Apr 21 08:56:51 SXPS13 NetworkManager: <debug> [1240318611.001895] periodic_update(): Roamed from BSSID (none) ((none)) to 00:19:E2:EC:BC:31 (KC) 
Apr 21 08:57:45 SXPS13 NetworkManager: <debug> [1240318665.002195] periodic_update(): Roamed from BSSID 00:19:E2:EC:BC:31 (KC) to (none) ((none)) 
Apr 21 08:57:51 SXPS13 NetworkManager: <debug> [1240318671.002011] periodic_update(): Roamed from BSSID (none) ((none)) to 00:19:E2:EC:BC:31 (KC) 
Apr 21 08:59:27 SXPS13 kernel: [  557.915410] ACPI: EC: GPE storm detected, transactions will use polling mode

```

Does anyone have any ideas? Also here is the output from lshw -C Network.

```

  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:dd:8a:62
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:5f:6f:bd:6a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.11.19 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d2:de:9d:71:76:33
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Any help would be great, it takes me about a half an hour of fiddling with the keyrings and what not to finally get connected. Also I have tried it on Linksys, Juniper and Netgear routers.

---

