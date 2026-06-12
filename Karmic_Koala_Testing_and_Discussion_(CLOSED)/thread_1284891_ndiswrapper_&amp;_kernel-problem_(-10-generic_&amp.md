---
title: "ndiswrapper &amp; kernel-problem (-10-generic &amp; -11-generic) (karmic)"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wompy on 2009-10-07
Hi,

I installed the Karmic alpha6 two weeks ago and surprisingly my wpa-connection worked,which i never get worked,since i am using ubuntu. After the update to the beta, the wpa-connectivity broke again. I now know,that i am able to use wpa with the -10-generic-kernel,but not with the -11-generic. Is there a way to use the -11-Kernel with wpa?

```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.31-10-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.31-10-generic SMP mod_unload modversions 586
```

```
Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
```

---

### Post by Sweevo on 2009-10-08
Hi

I just wanted to add a "me too" to this thread...

I've got a Medion Akoya E1312 Netbook with a Realtek RTL8192SE wlan using NDISWrapper.

This works on Karmic upto Kernel 2.6.31-10
 
Every kernel since then fails to connect. I've tried NetworkManager and WiCd, both try but then fail to connect to my WPA2 protected network.

I'm not sure which logs would be useful to post here, so any guidance would be really gratefully received

---

### Post by Sweevo on 2009-10-10
Hope you don't mind me bumping this thread, but I'm still experiencing the same problem after upgrading to kernel 2.6.31-13.

2.6.31-10 is still the most recent Kernel that actually allows me to connect.

Here the syslog from an unsuccessful attempt to connect under 2.6.31-13:

```
Oct 10 08:44:22 mark-laptop kernel: [  589.251450] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Oct 10 08:44:23 mark-laptop kernel: [  589.283462] ndiswrapper: driver net8192se (Realtek Semiconductor Corp.,05/20/2009,1080.7.0520.2009) loaded
Oct 10 08:44:23 mark-laptop kernel: [  589.283781] ndiswrapper 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 10 08:44:23 mark-laptop kernel: [  589.284662] ndiswrapper 0000:02:00.0: setting latency timer to 64
Oct 10 08:44:23 mark-laptop kernel: [  589.660065] ndiswrapper: using IRQ 16
Oct 10 08:44:23 mark-laptop kernel: [  590.097085] wlan0: ethernet device 00:25:d3:1d:43:87 using NDIS driver: net8192se, version: 0x500a5, NDIS version: 0x500, vendor: 'Realtek RTL8192SE Wireless LAN PCI-E NIC                                     ', 10EC:8172.5.conf
Oct 10 08:44:23 mark-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/wlan1, iface: wlan1)
Oct 10 08:44:23 mark-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Oct 10 08:44:23 mark-laptop NetworkManager: <info>  (wlan1): driver does not support SSID scans (scan_capa 0x00).
Oct 10 08:44:23 mark-laptop NetworkManager: <info>  (wlan1): new 802.11 WiFi device (driver: 'ndiswrapper')
Oct 10 08:44:23 mark-laptop NetworkManager: <info>  (wlan1): exported as /org/freedesktop/NetworkManager/Devices/2
Oct 10 08:44:23 mark-laptop NetworkManager: <info>  (wlan1): now managed
Oct 10 08:44:23 mark-laptop NetworkManager: <info>  (wlan1): device state change: 1 -> 2 (reason 2)
Oct 10 08:44:23 mark-laptop NetworkManager: <info>  (wlan1): bringing up device.
Oct 10 08:44:23 mark-laptop NetworkManager: <info>  (wlan1): preparing device.
Oct 10 08:44:23 mark-laptop NetworkManager: <info>  (wlan1): deactivating device (reason: 2).
Oct 10 08:44:23 mark-laptop NetworkManager: <info>  (wlan1): supplicant interface state:  starting -> ready
Oct 10 08:44:23 mark-laptop NetworkManager: <info>  (wlan1): device state change: 2 -> 3 (reason 42)
Oct 10 08:44:28 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-SCAN-RESULTS 
Oct 10 08:44:33 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 10 08:44:33 mark-laptop NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
Oct 10 08:44:33 mark-laptop NetworkManager: <info>  Activation (wlan1) starting connection 'Auto 73776565766F'
Oct 10 08:44:33 mark-laptop NetworkManager: <info>  (wlan1): device state change: 3 -> 4 (reason 0)
Oct 10 08:44:33 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 10 08:44:33 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Oct 10 08:44:33 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Oct 10 08:44:33 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Oct 10 08:44:33 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Oct 10 08:44:33 mark-laptop NetworkManager: <info>  (wlan1): device state change: 4 -> 5 (reason 0)
Oct 10 08:44:33 mark-laptop NetworkManager: <info>  Activation (wlan1/wireless): access point 'Auto 73776565766F' has security, but secrets are required.
Oct 10 08:44:33 mark-laptop NetworkManager: <info>  (wlan1): device state change: 5 -> 6 (reason 0)
Oct 10 08:44:33 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Oct 10 08:44:34 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-SCAN-RESULTS 
Oct 10 08:44:39 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> inactive
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  (wlan1): device state change: 6 -> 4 (reason 0)
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  (wlan1): device state change: 4 -> 5 (reason 0)
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Activation (wlan1/wireless): connection 'Auto 73776565766F' has security, and secrets exist.  No new secrets needed.
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Config: added 'ssid' value '73776565766F'
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Oct 10 08:44:45 mark-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 10 08:44:45 mark-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Oct 10 08:44:45 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  inactive -> scanning
Oct 10 08:44:54 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-SCAN-RESULTS 
Oct 10 08:44:54 mark-laptop wpa_supplicant[1253]: Trying to associate with 00:1f:33:01:d3:98 (SSID='73776565766F' freq=2462 MHz)
Oct 10 08:44:54 mark-laptop wpa_supplicant[1253]: Association request to the driver failed
Oct 10 08:44:54 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> associating
Oct 10 08:44:54 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  associating -> 4-way handshake
Oct 10 08:44:54 mark-laptop wpa_supplicant[1253]: Associated with 00:1f:33:01:d3:98
Oct 10 08:44:54 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> associated
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> 4-way handshake
Oct 10 08:44:55 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:44:55 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-CONNECTED - Connection to 00:1f:33:01:d3:98 completed (auth) [id=0 id_str=]
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '73776565766F'.
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  (wlan1): device state change: 5 -> 7 (reason 0)
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  Activation (wlan1) Beginning DHCP transaction (timeout in 45 seconds)
Oct 10 08:44:55 mark-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Oct 10 08:44:55 mark-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Oct 10 08:44:55 mark-laptop dhclient: All rights reserved.
Oct 10 08:44:55 mark-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  dhclient started with pid 7491
Oct 10 08:44:55 mark-laptop dhclient: 
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) started...
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) complete.
Oct 10 08:44:55 mark-laptop dhclient: Listening on LPF/wlan1/00:25:d3:1d:43:87
Oct 10 08:44:55 mark-laptop dhclient: Sending on   LPF/wlan1/00:25:d3:1d:43:87
Oct 10 08:44:55 mark-laptop dhclient: Sending on   Socket/fallback
Oct 10 08:44:55 mark-laptop NetworkManager: <info>  DHCP: device wlan1 state changed (null) -> preinit
Oct 10 08:44:56 mark-laptop avahi-daemon[991]: Registering new address record for fe80::225:d3ff:fe1d:4387 on wlan1.*.
Oct 10 08:44:56 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:44:56 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:44:56 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:44:56 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:44:57 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:44:57 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:44:57 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:44:57 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:44:58 mark-laptop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
Oct 10 08:44:58 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:44:58 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:44:58 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:44:58 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:01 mark-laptop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
Oct 10 08:45:02 mark-laptop wpa_supplicant[1253]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Oct 10 08:45:02 mark-laptop wpa_supplicant[1253]: Associated with 00:1f:33:01:d3:98
Oct 10 08:45:02 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> associated
Oct 10 08:45:03 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> 4-way handshake
Oct 10 08:45:03 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:03 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-CONNECTED - Connection to 00:1f:33:01:d3:98 completed (reauth) [id=0 id_str=]
Oct 10 08:45:03 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:03 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:04 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:04 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:04 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:04 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:05 mark-laptop kernel: [  590.097114] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Oct 10 08:45:05 mark-laptop kernel: [  590.107137] usbcore: registered new interface driver ndiswrapper
Oct 10 08:45:05 mark-laptop kernel: [  590.109048] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
Oct 10 08:45:05 mark-laptop kernel: [  590.109115] udev: renamed network interface wlan0 to wlan1
Oct 10 08:45:05 mark-laptop kernel: [  590.111975] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Oct 10 08:45:05 mark-laptop kernel: [  620.874066] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Oct 10 08:45:05 mark-laptop kernel: [  621.347856] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Oct 10 08:45:05 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:05 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:05 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:05 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:06 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:06 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:06 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:06 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:09 mark-laptop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
Oct 10 08:45:11 mark-laptop wpa_supplicant[1253]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Oct 10 08:45:11 mark-laptop wpa_supplicant[1253]: Associated with 00:1f:33:01:d3:98
Oct 10 08:45:11 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> associated
Oct 10 08:45:12 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> 4-way handshake
Oct 10 08:45:12 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:12 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-CONNECTED - Connection to 00:1f:33:01:d3:98 completed (reauth) [id=0 id_str=]
Oct 10 08:45:12 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:12 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:13 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:13 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:13 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:13 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:14 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:14 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:14 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:14 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:15 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:15 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:15 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:15 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:19 mark-laptop wpa_supplicant[1253]: Associated with 00:1f:33:01:d3:98
Oct 10 08:45:19 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> associated
Oct 10 08:45:20 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> 4-way handshake
Oct 10 08:45:20 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:20 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-CONNECTED - Connection to 00:1f:33:01:d3:98 completed (reauth) [id=0 id_str=]
Oct 10 08:45:20 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:20 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:21 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:21 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:21 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:21 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:22 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:22 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:22 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:22 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:23 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:23 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:23 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:23 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:24 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-SCAN-RESULTS 
Oct 10 08:45:24 mark-laptop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
Oct 10 08:45:27 mark-laptop wpa_supplicant[1253]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Oct 10 08:45:27 mark-laptop wpa_supplicant[1253]: Associated with 00:1f:33:01:d3:98
Oct 10 08:45:27 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> associated
Oct 10 08:45:28 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> 4-way handshake
Oct 10 08:45:28 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:28 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-CONNECTED - Connection to 00:1f:33:01:d3:98 completed (reauth) [id=0 id_str=]
Oct 10 08:45:28 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:28 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:29 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:29 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:29 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:29 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:30 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:30 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:30 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:30 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:31 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:31 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:31 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:31 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:36 mark-laptop dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14
Oct 10 08:45:36 mark-laptop wpa_supplicant[1253]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Oct 10 08:45:36 mark-laptop wpa_supplicant[1253]: Associated with 00:1f:33:01:d3:98
Oct 10 08:45:36 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> associated
Oct 10 08:45:37 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> 4-way handshake
Oct 10 08:45:37 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:37 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-CONNECTED - Connection to 00:1f:33:01:d3:98 completed (reauth) [id=0 id_str=]
Oct 10 08:45:37 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:37 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:38 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:38 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:38 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:38 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:39 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:39 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:39 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:39 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:40 mark-laptop wpa_supplicant[1253]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:45:40 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> 4-way handshake
Oct 10 08:45:40 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:45:40 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:45:41 mark-laptop NetworkManager: <info>  (wlan1): DHCP transaction took too long, stopping it.
Oct 10 08:45:41 mark-laptop NetworkManager: <info>  (wlan1): canceled DHCP transaction, dhcp client pid 7491
Oct 10 08:45:41 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Oct 10 08:45:41 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) started...
Oct 10 08:45:41 mark-laptop NetworkManager: <info>  (wlan1): device state change: 7 -> 9 (reason 5)
Oct 10 08:45:41 mark-laptop NetworkManager: <info>  Activation (wlan1) failed for access point (73776565766F)
Oct 10 08:45:41 mark-laptop NetworkManager: <info>  Marking connection 'Auto 73776565766F' invalid.
Oct 10 08:45:41 mark-laptop NetworkManager: <info>  Activation (wlan1) failed.
Oct 10 08:45:41 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) complete.
Oct 10 08:45:41 mark-laptop NetworkManager: <info>  (wlan1): device state change: 9 -> 3 (reason 0)
Oct 10 08:45:41 mark-laptop NetworkManager: <info>  (wlan1): deactivating device (reason: 0).
Oct 10 08:45:53 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 10 08:46:14 mark-laptop wpa_supplicant[1253]: CTRL-EVENT-SCAN-RESULTS 
```

And here is a successful connection under 2.6.31-10

```
Oct 10 08:53:22 mark-laptop kernel: [  179.506401] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Oct 10 08:53:22 mark-laptop kernel: [  179.533591] ndiswrapper: driver net8192se (Realtek Semiconductor Corp.,05/20/2009,1080.7.0520.2009) loaded
Oct 10 08:53:22 mark-laptop kernel: [  179.533882] ndiswrapper 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 10 08:53:22 mark-laptop kernel: [  179.534783] ndiswrapper 0000:02:00.0: setting latency timer to 64
Oct 10 08:53:22 mark-laptop kernel: [  179.732069] ndiswrapper: using IRQ 16
Oct 10 08:53:22 mark-laptop kernel: [  180.119065] wlan0: ethernet device 00:25:d3:1d:43:87 using NDIS driver: net8192se, version: 0x500a5, NDIS version: 0x500, vendor: 'Realtek RTL8192SE Wireless LAN PCI-E NIC                                     ', 10EC:8172.5.conf
Oct 10 08:53:22 mark-laptop kernel: [  180.119097] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Oct 10 08:53:22 mark-laptop kernel: [  180.124759] usbcore: registered new interface driver ndiswrapper
Oct 10 08:53:22 mark-laptop kernel: [  180.127690] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
Oct 10 08:53:22 mark-laptop NetworkManager: <info>  (wlan1): driver does not support SSID scans (scan_capa 0x00).
Oct 10 08:53:22 mark-laptop NetworkManager: <info>  (wlan1): new 802.11 WiFi device (driver: 'ndiswrapper')
Oct 10 08:53:22 mark-laptop NetworkManager: <info>  (wlan1): exported as /org/freedesktop/NetworkManager/Devices/2
Oct 10 08:53:22 mark-laptop NetworkManager: <info>  (wlan1): now managed
Oct 10 08:53:22 mark-laptop NetworkManager: <info>  (wlan1): device state change: 1 -> 2 (reason 2)
Oct 10 08:53:22 mark-laptop NetworkManager: <info>  (wlan1): bringing up device.
Oct 10 08:53:22 mark-laptop NetworkManager: <info>  (wlan1): preparing device.
Oct 10 08:53:22 mark-laptop NetworkManager: <info>  (wlan1): deactivating device (reason: 2).
Oct 10 08:53:22 mark-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/wlan1, iface: wlan1)
Oct 10 08:53:22 mark-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Oct 10 08:53:22 mark-laptop NetworkManager: <info>  (wlan1): supplicant interface state:  starting -> ready
Oct 10 08:53:22 mark-laptop NetworkManager: <info>  (wlan1): device state change: 2 -> 3 (reason 42)
Oct 10 08:53:27 mark-laptop wpa_supplicant[1075]: CTRL-EVENT-SCAN-RESULTS 
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) starting connection 'Auto 73776565766F'
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  (wlan1): device state change: 3 -> 4 (reason 0)
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  (wlan1): device state change: 4 -> 5 (reason 0)
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1/wireless): access point 'Auto 73776565766F' has security, but secrets are required.
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  (wlan1): device state change: 5 -> 6 (reason 0)
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  (wlan1): device state change: 6 -> 4 (reason 0)
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  (wlan1): device state change: 4 -> 5 (reason 0)
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1/wireless): connection 'Auto 73776565766F' has security, and secrets exist.  No new secrets needed.
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Config: added 'ssid' value '73776565766F'
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Oct 10 08:53:27 mark-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 10 08:53:27 mark-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Oct 10 08:53:27 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Oct 10 08:53:32 mark-laptop wpa_supplicant[1075]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 10 08:53:32 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Oct 10 08:53:37 mark-laptop wpa_supplicant[1075]: CTRL-EVENT-SCAN-RESULTS 
Oct 10 08:53:37 mark-laptop wpa_supplicant[1075]: Trying to associate with 00:1f:33:01:d3:98 (SSID='73776565766F' freq=2462 MHz)
Oct 10 08:53:37 mark-laptop wpa_supplicant[1075]: Association request to the driver failed
Oct 10 08:53:37 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> associating
Oct 10 08:53:37 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  associating -> 4-way handshake
Oct 10 08:53:37 mark-laptop wpa_supplicant[1075]: Associated with 00:1f:33:01:d3:98
Oct 10 08:53:37 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> associated
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> 4-way handshake
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> group handshake
Oct 10 08:53:38 mark-laptop wpa_supplicant[1075]: WPA: Key negotiation completed with 00:1f:33:01:d3:98 [PTK=CCMP GTK=CCMP]
Oct 10 08:53:38 mark-laptop wpa_supplicant[1075]: CTRL-EVENT-CONNECTED - Connection to 00:1f:33:01:d3:98 completed (auth) [id=0 id_str=]
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '73776565766F'.
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  (wlan1): device state change: 5 -> 7 (reason 0)
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  Activation (wlan1) Beginning DHCP transaction (timeout in 45 seconds)
Oct 10 08:53:38 mark-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Oct 10 08:53:38 mark-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Oct 10 08:53:38 mark-laptop dhclient: All rights reserved.
Oct 10 08:53:38 mark-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Oct 10 08:53:38 mark-laptop dhclient: 
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  dhclient started with pid 3730
Oct 10 08:53:38 mark-laptop dhclient: Listening on LPF/wlan1/00:25:d3:1d:43:87
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct 10 08:53:38 mark-laptop dhclient: Sending on   LPF/wlan1/00:25:d3:1d:43:87
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Oct 10 08:53:38 mark-laptop dhclient: Sending on   Socket/fallback
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  DHCP: device wlan1 state changed normal exit -> preinit
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) started...
Oct 10 08:53:38 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) complete.
Oct 10 08:53:39 mark-laptop avahi-daemon[847]: Registering new address record for fe80::225:d3ff:fe1d:4387 on wlan1.*.
Oct 10 08:53:41 mark-laptop dhclient: DHCPREQUEST of 192.168.0.4 on wlan1 to 255.255.255.255 port 67
Oct 10 08:53:41 mark-laptop dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Oct 10 08:53:41 mark-laptop NetworkManager: <info>  DHCP: device wlan1 state changed preinit -> reboot
Oct 10 08:53:41 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 10 08:53:41 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) started...
Oct 10 08:53:41 mark-laptop NetworkManager: <info>    address 192.168.0.4
Oct 10 08:53:41 mark-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Oct 10 08:53:41 mark-laptop NetworkManager: <info>    gateway 192.168.0.1
Oct 10 08:53:41 mark-laptop NetworkManager: <info>    nameserver '208.67.222.222'
Oct 10 08:53:41 mark-laptop NetworkManager: <info>    nameserver '208.67.220.220'
Oct 10 08:53:41 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) scheduled...
Oct 10 08:53:41 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) complete.
Oct 10 08:53:41 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) started...
Oct 10 08:53:41 mark-laptop avahi-daemon[847]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.0.4.
Oct 10 08:53:41 mark-laptop avahi-daemon[847]: New relevant interface wlan1.IPv4 for mDNS.
Oct 10 08:53:41 mark-laptop avahi-daemon[847]: Registering new address record for 192.168.0.4 on wlan1.IPv4.
Oct 10 08:53:41 mark-laptop dhclient: bound to 192.168.0.4 -- renewal in 106793 seconds.
Oct 10 08:53:42 mark-laptop NetworkManager: <info>  (wlan1): device state change: 7 -> 8 (reason 0)
Oct 10 08:53:42 mark-laptop NetworkManager: <info>  Policy set 'Auto 73776565766F' (wlan1) as default for routing and DNS.
Oct 10 08:53:42 mark-laptop NetworkManager: <info>  Activation (wlan1) successful, device activated.
Oct 10 08:53:42 mark-laptop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) complete.
Oct 10 08:53:42 mark-laptop ntpdate[3822]: adjust time server 91.189.94.4 offset -0.291434 sec
Oct 10 08:53:53 mark-laptop wpa_supplicant[1075]: CTRL-EVENT-SCAN-RESULTS 
```

I even tried changing my router from WPA2 to WEP encryption - but that failed to connect under 2.6.31-13 as well.

Do any of you think that this is a bug worth logging? If so, which package should I log it against?

Thanks

Sweevo

---

### Post by Sweevo on 2009-10-10
Ok - quick update, I've managed to get it working...

After Googling for most of the morning, I've found a really helpful post here: [Ubuntuusers.de]("http://translate.google.co.uk/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/topic/medion-akoya-mini-e1312-md-97690/3/&ei=S6lwSoaxBs-rjAfJh42dBQ&sa=X&oi=translate&resnum=4&ct=result&prev=/search%3Fq%3De1312%2Blinux%26hl%3Den%26sa%3DN%26tbo%3D1%26tbs%3Dfrm:1")

Eseentially, by issuing this command during a connection attempt:

```
sudo renice +19 $(pidof wpa_supplicant)
```

I successfully connect every time.

So my question now is - Why do I need to do this now, when it wasn't necessary in older kernels?

Also - is there any way to automate this?

Thanks

Sweevo

---

### Post by wompy on 2009-10-15
Thanks Sweevo for your solution, it works for me too.

Did you get more information about the question, why the new kernels not work?

---

### Post by Sweevo on 2009-10-19
No - I never did find out why, but I've now been given a proper linux driver for my card (see the bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126")) which means that I don't have to use ndiswrapper any longer. It appears that it was ndiswrapper which was causing my problem, or at least the windows driver which it was using.

Some forums which I've read suggest that poorly written windows drivers can cause this type of problem due to a timing issue as they're loaded, but I don't know if this is true or not.

I have to say that it was really annoying having to run that command at each login, I think if it had gone on much longer I was have logged a bug on launchpad - it may be worth you doing it, we can't be the only people with the problem.

Kind regards

Sweevo

---

