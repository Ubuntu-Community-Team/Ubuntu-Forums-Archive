---
title: "Karmic PPTP problems"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by subvertbeats on 2009-09-29
Hi

Im having problems with PPTP in Karmic - unable to establish a connection.

Ive searched other threads and have set all the options as advised (uncheck EAP, checked MPPE, username set to domain/username)

Heres the relevant sections from my daemon.log

Any ideas?

Many thanks in advance,


Sep 29 12:33:20 bwilliams-t60p NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Sep 29 12:33:20 bwilliams-t60p NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 4448
Sep 29 12:33:20 bwilliams-t60p NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Sep 29 12:33:20 bwilliams-t60p NetworkManager: <info>  VPN plugin state changed: 1
Sep 29 12:33:21 bwilliams-t60p NetworkManager: <info>  VPN plugin state changed: 3
Sep 29 12:33:21 bwilliams-t60p NetworkManager: <info>  VPN connection 'TLOGIC' (Connect) reply received.
Sep 29 12:33:21 bwilliams-t60p NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 29 12:33:21 bwilliams-t60p NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no exported connection
Sep 29 12:33:21 bwilliams-t60p pptp[4453]: nm-pptp-service-4448 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Sep 29 12:33:52 bwilliams-t60p NetworkManager: <info>  VPN plugin failed: 1
Sep 29 12:33:52 bwilliams-t60p NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 29 12:33:52 bwilliams-t60p NetworkManager: <info>  VPN plugin failed: 1
Sep 29 12:33:56 bwilliams-t60p wpa_supplicant[1160]: CTRL-EVENT-SCAN-RESULTS 
Sep 29 12:33:57 bwilliams-t60p NetworkManager: <info>  VPN plugin failed: 1
Sep 29 12:33:57 bwilliams-t60p NetworkManager: <info>  VPN plugin state changed: 6
Sep 29 12:33:57 bwilliams-t60p NetworkManager: <info>  VPN plugin state change reason: 0
Sep 29 12:33:57 bwilliams-t60p NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Sep 29 12:33:57 bwilliams-t60p NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Sep 29 12:34:09 bwilliams-t60p NetworkManager: <debug> [1254224049.002358] ensure_killed(): waiting for vpn service pid 4448 to exit
Sep 29 12:34:09 bwilliams-t60p NetworkManager: <debug> [1254224049.002513] ensure_killed(): vpn service pid 4448 cleaned up
Sep 29 12:35:56 bwilliams-t60p wpa_supplicant[1160]: CTRL-EVENT-SCAN-RESULTS 
Sep 29 12:36:30 bwilliams-t60p pptp[4454]: nm-pptp-service-4448 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection timed out
Sep 29 12:36:30 bwilliams-t60p pptp[4454]: nm-pptp-service-4448 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 63.87.243.65
Sep 29 12:36:30 bwilliams-t60p pptp[4453]: nm-pptp-service-4448 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256

---

