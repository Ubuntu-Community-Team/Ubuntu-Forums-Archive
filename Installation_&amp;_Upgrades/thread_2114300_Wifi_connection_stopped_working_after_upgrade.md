---
title: "Wifi connection stopped working after upgrade"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by 6re6or on 2013-02-09
Hi,
My wifi connection has been working flawlessly for 2 years running first ubuntu 11.04 and gradually upgrading to 12.04. A few minutes ago the connection to my router suddenly stopped working after a restart (it had been connected right up until the restart). The network icon on top shows that it is trying to connect and after a while it stops and tells me I am disconnected. All other devices (3) connected to the router continue to access as usual so I do not think it has anything to do with the router itself. Also I found out that I have no problem connecting to the hotspot of my cell phone.

Also I have reinstalled my laptop and during installation the wifi is present as wlan0 but after upgrade its changed to eth1.

Any ideas on what the problem might be? Tips on how to debug it?
Thank you for your time and help.

lspci:
24:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

syslog:
Feb 9 23:58:14 ProBook NetworkManager[963]: <info> Activation (eth1) starting connection 'wireless'
Feb 9 23:58:14 ProBook NetworkManager[963]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 9 23:58:14 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 9 23:58:14 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 9 23:58:14 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 9 23:58:14 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 9 23:58:14 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 9 23:58:14 ProBook NetworkManager[963]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 9 23:58:14 ProBook NetworkManager[963]: <info> Activation (eth1/wireless): access point 'wireless' has security, but secrets are required.
Feb 9 23:58:14 ProBook NetworkManager[963]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 9 23:58:14 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 9 23:58:24 ProBook NetworkManager[963]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Activation (eth1/wireless): connection 'wireless' has security, and secrets exist. No new secrets needed.
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Config: added 'ssid' value 'wireless'
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Config: added 'scan_ssid' value '1'
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Config: added 'psk' value '<omitted>'
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> Config: set interface ap_scan to 1
Feb 9 23:58:24 ProBook NetworkManager[963]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 9 23:58:26 ProBook wpa_supplicant[1159]: Trying to associate with 00:14:bf:dc:74:26 (SSID='wireless' freq=2462 MHz)
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 9 23:58:26 ProBook wpa_supplicant[1159]: Associated with 00:14:bf:dc:74:26
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 9 23:58:26 ProBook wpa_supplicant[1159]: WPA: Key negotiation completed with 00:14:bf:dc:74:26 [PTK=CCMP GTK=TKIP]
Feb 9 23:58:26 ProBook wpa_supplicant[1159]: CTRL-EVENT-CONNECTED - Connection to 00:14:bf:dc:74:26 completed (reauth) [id=0 id_str=].
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> (eth1): supplicant interface state: 4-way handshake -> completed
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful. Connected to wireless network 'wireless'.
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> dhclient started with pid 2897
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> Activation (eth1) Beginning IP6 addrconf.
Feb 9 23:58:26 ProBook dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Feb 9 23:58:26 ProBook dhclient: Copyright 2004-2011 Internet Systems Consortium.
Feb 9 23:58:26 ProBook dhclient: All rights reserved.
Feb 9 23:58:26 ProBook dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Feb 9 23:58:26 ProBook dhclient:
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Feb 9 23:58:26 ProBook NetworkManager[963]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Feb 9 23:58:26 ProBook dhclient: Listening on LPF/eth1/ac:81:12:7a:e7:15
Feb 9 23:58:26 ProBook dhclient: Sending on LPF/eth1/ac:81:12:7a:e7:15
Feb 9 23:58:26 ProBook dhclient: Sending on Socket/fallback
Feb 9 23:58:26 ProBook dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Feb 9 23:58:27 ProBook kernel: [ 532.100792] net_ratelimit: 2 callbacks suppressed
Feb 9 23:58:27 ProBook kernel: [ 532.100800] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:27 ProBook kernel: [ 532.100808] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:27 ProBook kernel: [ 532.100902] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:27 ProBook kernel: [ 532.100908] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:27 ProBook kernel: [ 532.175977] userif-2: sent link down event.
Feb 9 23:58:29 ProBook kernel: [ 532.175986] userif-2: sent link up event.
Feb 9 23:58:29 ProBook kernel: [ 534.098661] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:29 ProBook kernel: [ 534.098676] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:29 ProBook kernel: [ 534.098755] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:29 ProBook kernel: [ 534.098765] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:29 ProBook dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Feb 9 23:58:31 ProBook kernel: [ 536.095427] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:31 ProBook kernel: [ 536.095440] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:32 ProBook dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Feb 9 23:58:33 ProBook kernel: [ 538.093497] net_ratelimit: 2 callbacks suppressed
Feb 9 23:58:33 ProBook kernel: [ 538.093509] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:33 ProBook kernel: [ 538.093521] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:33 ProBook kernel: [ 538.093610] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:33 ProBook kernel: [ 538.093620] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:35 ProBook kernel: [ 540.091000] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:35 ProBook kernel: [ 540.091015] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:35 ProBook kernel: [ 540.091098] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:35 ProBook kernel: [ 540.091107] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:36 ProBook dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Feb 9 23:58:37 ProBook kernel: [ 542.090018] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:37 ProBook kernel: [ 542.090033] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:37 ProBook kernel: [ 542.467682] eth1: no IPv6 routers present
Feb 9 23:58:39 ProBook kernel: [ 544.087855] net_ratelimit: 2 callbacks suppressed
Feb 9 23:58:39 ProBook kernel: [ 544.087863] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:39 ProBook kernel: [ 544.087872] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:39 ProBook kernel: [ 544.087953] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:39 ProBook kernel: [ 544.087960] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:41 ProBook kernel: [ 546.086300] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:41 ProBook kernel: [ 546.086312] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:41 ProBook kernel: [ 546.086377] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:41 ProBook kernel: [ 546.086383] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:43 ProBook kernel: [ 548.084184] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:43 ProBook kernel: [ 548.084201] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:45 ProBook kernel: [ 550.081663] net_ratelimit: 2 callbacks suppressed
Feb 9 23:58:45 ProBook kernel: [ 550.081670] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:45 ProBook kernel: [ 550.081679] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:45 ProBook kernel: [ 550.081740] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:45 ProBook kernel: [ 550.081747] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:47 ProBook kernel: [ 552.079296] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:47 ProBook kernel: [ 552.079310] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:47 ProBook kernel: [ 552.079373] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:47 ProBook kernel: [ 552.079379] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:47 ProBook NetworkManager[963]: <info> (eth1): IP6 addrconf timed out or failed.
Feb 9 23:58:47 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Feb 9 23:58:47 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Feb 9 23:58:47 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Feb 9 23:58:47 ProBook dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Feb 9 23:58:49 ProBook kernel: [ 554.076436] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:49 ProBook kernel: [ 554.076442] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:51 ProBook kernel: [ 556.074239] net_ratelimit: 2 callbacks suppressed
Feb 9 23:58:51 ProBook kernel: [ 556.074242] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:51 ProBook kernel: [ 556.074245] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:51 ProBook kernel: [ 556.074277] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:51 ProBook kernel: [ 556.074280] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:53 ProBook kernel: [ 558.072589] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:53 ProBook kernel: [ 558.072604] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:53 ProBook kernel: [ 558.072691] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:53 ProBook kernel: [ 558.072702] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:55 ProBook kernel: [ 560.071460] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:55 ProBook kernel: [ 560.071476] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:57 ProBook kernel: [ 562.068909] net_ratelimit: 2 callbacks suppressed
Feb 9 23:58:57 ProBook kernel: [ 562.068918] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:57 ProBook kernel: [ 562.068932] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:57 ProBook kernel: [ 562.069094] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:57 ProBook kernel: [ 562.069106] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:58 ProBook dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
Feb 9 23:58:59 ProBook kernel: [ 564.067583] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:59 ProBook kernel: [ 564.067601] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:58:59 ProBook kernel: [ 564.067691] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:58:59 ProBook kernel: [ 564.067702] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:01 ProBook kernel: [ 566.066124] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:01 ProBook kernel: [ 566.066142] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:03 ProBook kernel: [ 568.062417] net_ratelimit: 2 callbacks suppressed
Feb 9 23:59:03 ProBook kernel: [ 568.062427] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:03 ProBook kernel: [ 568.062439] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:03 ProBook kernel: [ 568.062527] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:03 ProBook kernel: [ 568.062536] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:05 ProBook kernel: [ 570.060953] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:05 ProBook kernel: [ 570.060970] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:05 ProBook kernel: [ 570.061064] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:05 ProBook kernel: [ 570.061074] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:07 ProBook kernel: [ 572.058705] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:07 ProBook kernel: [ 572.058721] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:09 ProBook kernel: [ 574.056205] net_ratelimit: 2 callbacks suppressed
Feb 9 23:59:09 ProBook kernel: [ 574.056214] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:09 ProBook kernel: [ 574.056226] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:09 ProBook kernel: [ 574.056699] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:09 ProBook kernel: [ 574.056709] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:11 ProBook kernel: [ 576.055785] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:11 ProBook kernel: [ 576.055800] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:11 ProBook kernel: [ 576.055881] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:11 ProBook kernel: [ 576.055891] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:12 ProBook NetworkManager[963]: <warn> (eth1): DHCPv4 request timed out.
Feb 9 23:59:12 ProBook NetworkManager[963]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2897
Feb 9 23:59:12 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Feb 9 23:59:12 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Feb 9 23:59:12 ProBook NetworkManager[963]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Feb 9 23:59:12 ProBook NetworkManager[963]: <warn> Activation (eth1) failed for access point (wireless)
Feb 9 23:59:12 ProBook NetworkManager[963]: <warn> Activation (eth1) failed.
Feb 9 23:59:12 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Feb 9 23:59:12 ProBook NetworkManager[963]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 9 23:59:12 ProBook NetworkManager[963]: <info> (eth1): deactivating device (reason 'none') [0]
Feb 9 23:59:12 ProBook kernel: [ 577.268109] cfg80211: All devices are disconnected, going to restore regulatory settings
Feb 9 23:59:12 ProBook kernel: [ 577.268120] cfg80211: Restoring regulatory settings
Feb 9 23:59:12 ProBook kernel: [ 577.268132] cfg80211: Calling CRDA to update world regulatory domain
Feb 9 23:59:12 ProBook wpa_supplicant[1159]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Feb 9 23:59:12 ProBook NetworkManager[963]: <info> (eth1): supplicant interface state: completed -> disconnected
Feb 9 23:59:12 ProBook kernel: [ 577.277960] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.277964] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.277966] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.277968] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.277969] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.277971] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.277973] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.277975] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.277976] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.277978] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.277980] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.277982] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.277983] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.277985] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.277987] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.277989] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.277990] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.277992] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.277994] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.277996] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.277997] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.277999] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278001] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278003] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278004] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278006] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278008] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278010] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278011] cfg80211: Disabling freq 5170 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278013] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278015] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278016] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278018] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278020] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278022] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278023] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278025] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278027] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278029] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278030] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278032] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278034] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278036] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278037] cfg80211: Disabling freq 5260 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278039] cfg80211: Disabling freq 5280 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278040] cfg80211: Disabling freq 5300 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278041] cfg80211: Disabling freq 5320 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278042] cfg80211: Disabling freq 5500 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278043] cfg80211: Disabling freq 5520 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278044] cfg80211: Disabling freq 5540 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278045] cfg80211: Disabling freq 5560 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278046] cfg80211: Disabling freq 5580 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278047] cfg80211: Disabling freq 5600 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278048] cfg80211: Disabling freq 5620 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278049] cfg80211: Disabling freq 5640 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278050] cfg80211: Disabling freq 5660 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278051] cfg80211: Disabling freq 5680 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278052] cfg80211: Disabling freq 5700 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278054] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278056] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278057] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278059] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278061] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278063] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278064] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278066] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278068] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Feb 9 23:59:12 ProBook kernel: [ 577.278070] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278071] cfg80211: Disabling freq 5920 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278072] cfg80211: Disabling freq 5940 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278073] cfg80211: Disabling freq 5960 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278074] cfg80211: Disabling freq 5980 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278076] cfg80211: Disabling freq 6000 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278077] cfg80211: Disabling freq 6020 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278078] cfg80211: Disabling freq 6040 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278079] cfg80211: Disabling freq 6060 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278080] cfg80211: Disabling freq 6080 MHz
Feb 9 23:59:12 ProBook kernel: [ 577.278083] cfg80211: World regulatory domain updated:
Feb 9 23:59:12 ProBook kernel: [ 577.278084] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 9 23:59:12 ProBook kernel: [ 577.278086] cfg80211: (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278088] cfg80211: (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278089] cfg80211: (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278091] cfg80211: (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.278093] cfg80211: (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 9 23:59:12 ProBook kernel: [ 577.467686] userif-2: sent link down event.
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Auto-activating connection 'HTC Portable Hotspot 56DA'.
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) starting connection 'HTC Portable Hotspot 56DA'
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1/wireless): access point 'HTC Portable Hotspot 56DA' has security, but secrets are required.
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1/wireless): connection 'HTC Portable Hotspot 56DA' has security, and secrets exist. No new secrets needed.
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Config: added 'ssid' value 'HTC Portable Hotspot 56DA'
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Config: added 'scan_ssid' value '1'
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Config: added 'psk' value '<omitted>'
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> Config: set interface ap_scan to 1
Feb 9 23:59:15 ProBook NetworkManager[963]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 9 23:59:16 ProBook wpa_supplicant[1159]: Trying to associate with a0:f4:50:f3:e6:4a (SSID='HTC Portable Hotspot 56DA' freq=2437 MHz)
Feb 9 23:59:16 ProBook NetworkManager[963]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 9 23:59:16 ProBook wpa_supplicant[1159]: Associated with a0:f4:50:f3:e6:4a
Feb 9 23:59:16 ProBook NetworkManager[963]: <info> (eth1): supplicant interface state: associating -> associated
Feb 9 23:59:16 ProBook NetworkManager[963]: <info> (eth1): supplicant interface state: associated -> 4-way handshake
Feb 9 23:59:17 ProBook kernel: [ 577.467695] userif-2: sent link up event.
Feb 9 23:59:17 ProBook kernel: [ 582.049726] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:17 ProBook kernel: [ 582.049740] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:17 ProBook kernel: [ 582.049966] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Feb 9 23:59:17 ProBook kernel: [ 582.049978] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Feb 9 23:59:17 ProBook wpa_supplicant[1159]: WPA: Key negotiation completed with a0:f4:50:f3:e6:4a [PTK=CCMP GTK=CCMP]
Feb 9 23:59:17 ProBook wpa_supplicant[1159]: CTRL-EVENT-CONNECTED - Connection to a0:f4:50:f3:e6:4a completed (reauth) [id=0 id_str=]
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> (eth1): supplicant interface state: 4-way handshake -> completed
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful. Connected to wireless network 'HTC Portable Hotspot 56DA'.
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> dhclient started with pid 2953
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> Activation (eth1) Beginning IP6 addrconf.
Feb 9 23:59:17 ProBook dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Feb 9 23:59:17 ProBook dhclient: Copyright 2004-2011 Internet Systems Consortium.
Feb 9 23:59:17 ProBook dhclient: All rights reserved.
Feb 9 23:59:17 ProBook dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Feb 9 23:59:17 ProBook dhclient:
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Feb 9 23:59:17 ProBook dhclient: Listening on LPF/eth1/ac:81:12:7a:e7:15
Feb 9 23:59:17 ProBook dhclient: Sending on LPF/eth1/ac:81:12:7a:e7:15
Feb 9 23:59:17 ProBook dhclient: Sending on Socket/fallback
Feb 9 23:59:17 ProBook dhclient: DHCPREQUEST of 192.168.1.59 on eth1 to 255.255.255.255 port 67
Feb 9 23:59:17 ProBook dhclient: DHCPACK of 192.168.1.59 from 192.168.1.1
Feb 9 23:59:17 ProBook dhclient: bound to 192.168.1.59 -- renewal in 1367 seconds.
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> address 192.168.1.59
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> prefix 24 (255.255.255.0)
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> gateway 192.168.1.1
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> hostname 'ProBook'
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> nameserver '192.168.1.1'
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Feb 9 23:59:17 ProBook NetworkManager[963]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...

---

