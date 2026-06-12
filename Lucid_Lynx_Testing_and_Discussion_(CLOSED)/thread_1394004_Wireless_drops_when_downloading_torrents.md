---
title: "Wireless drops when downloading torrents"
date: 2010-01-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zaphod777 on 2010-01-30
Hello everyone.

I just installed 10.04 on a new HDD to see if this issue is still present in 10.04 as it is in 9.10 and it is but not as bad.

When I am downloading torrents my wireless will randomly disconnect and re-connect. A lot of users are experiencing this issue it would be nice if we could get a fix before the next release.

Here is my log file of the event.

Jan 30 16:34:57 zaphod dhclient: DHCPREQUEST of 192.168.11.100 on wlan0 to 255.255.255.255 port 67
Jan 30 16:34:57 zaphod dhclient: DHCPACK of 192.168.11.100 from 192.168.11.1
Jan 30 16:34:57 zaphod dhclient: bound to 192.168.11.100 -- renewal in 68003 seconds.
Jan 30 16:34:57 zaphod NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Jan 30 16:34:57 zaphod NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 30 16:34:57 zaphod NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 30 16:34:57 zaphod NetworkManager: <info>    address 192.168.11.100
Jan 30 16:34:57 zaphod NetworkManager: <info>    prefix 24 (255.255.255.0)
Jan 30 16:34:57 zaphod NetworkManager: <info>    gateway 192.168.11.1
Jan 30 16:34:57 zaphod NetworkManager: <info>    nameserver '192.168.11.1'
Jan 30 16:34:57 zaphod NetworkManager: <info>    domain name 'chgsk1.kt.home.ne.jp'
Jan 30 16:34:57 zaphod NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 30 16:34:57 zaphod NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 30 16:34:57 zaphod NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan 30 16:34:57 zaphod avahi-daemon[1145]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.11.100.
Jan 30 16:34:57 zaphod avahi-daemon[1145]: New relevant interface wlan0.IPv4 for mDNS.
Jan 30 16:34:57 zaphod avahi-daemon[1145]: Registering new address record for 192.168.11.100 on wlan0.IPv4.
Jan 30 16:34:58 zaphod NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jan 30 16:34:58 zaphod NetworkManager: <info>  Policy set 'Auto 42' (wlan0) as default for routing and DNS.
Jan 30 16:34:58 zaphod NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jan 30 16:34:58 zaphod NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 30 16:34:59 zaphod kernel: [ 4570.178391] iwlagn 0000:0b:00.0: iwl_tx_agg_start on ra = 00:1d:73:8e:de:98 tid = 0
Jan 30 16:34:59 zaphod ntpdate[4841]: adjust time server 91.189.94.4 offset -0.060704 sec

---

### Post by zaphod777 on 2010-01-30
Okay after tons of searching I think I have found a fix

according to this post 
[http://lists.us.dell.com/pipermail/linux-desktops/2009-November/003324.html](http://lists.us.dell.com/pipermail/linux-desktops/2009-November/003324.html)

I need to add

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```
to the grub2 boot parameters 

on the file located 

 /etc/default/grub

Hopefully this will do the trick since it has been a very aggravating bug. 

I will report back on the issue. I know a lot of people with my card and other intel cards are really having a hard time.

---

### Post by jfernyhough on 2010-01-30
Yup, the Intel 2200bg is a rubbish card when it's used (even in Windows). The 3945abg was a lot better (though the driver on the company Windows installation sucks, was fine on my old laptop, and it's fine in Linux). My 5100agn is pretty solid.

I know it's not the ideal approach (though probably the easiest), but I'd look at getting a new card if you're going to be using wifi a lot. :)

I'll have to try the noapic switch, though. That might be useful on the older laptops I have to use from time to time.

---

### Post by zaphod777 on 2010-01-30
Mine has the  intel 4965 abgn card and even after that "fix" it has dropped out a lot however I think manually setting the BSSID seams to have maybe fixed it. 

It seams that without it the WLAN keeps scanning the wireless networks every few seconds and finally making the connection timeout.  

time will tell I am trying to hit the WLAN pretty hard right now and see. 

What card would you recommend for an xps1530 that is linux freindly and wireless n?

right now the network seamed to hang but not time out or disconnect 

logs below:

Jan 30 23:34:36 zaphod kernel: [15893.164955] iwlagn 0000:0b:00.0: iwl_tx_agg_start on ra = 02:1d:73:8e:de:98 tid = 0
Jan 30 23:36:39 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:38:40 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:40:40 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:42:40 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:44:42 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:46:03 zaphod kernel: [16579.817501] wlan0: deauthenticated from 02:1d:73:8e:de:98 (Reason: 6)
Jan 30 23:46:03 zaphod wpa_supplicant[1381]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan 30 23:46:03 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jan 30 23:46:03 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 30 23:46:05 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:46:05 zaphod wpa_supplicant[1381]: WPS-AP-AVAILABLE 
Jan 30 23:46:05 zaphod wpa_supplicant[1381]: Trying to associate with 02:1d:73:8e:de:98 (SSID='44' freq=2457 MHz)
Jan 30 23:46:05 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 30 23:46:05 zaphod kernel: [16581.839121] wlan0: direct probe to AP 02:1d:73:8e:de:98 (try 1)
Jan 30 23:46:05 zaphod kernel: [16581.859313] wlan0: direct probe responded
Jan 30 23:46:05 zaphod kernel: [16581.859319] wlan0: authenticate with AP 02:1d:73:8e:de:98 (try 1)
Jan 30 23:46:05 zaphod kernel: [16581.861079] wlan0: authenticated
Jan 30 23:46:05 zaphod kernel: [16581.861102] wlan0: associate with AP 02:1d:73:8e:de:98 (try 1)
Jan 30 23:46:05 zaphod kernel: [16581.865888] wlan0: RX ReassocResp from 02:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan 30 23:46:05 zaphod kernel: [16581.865892] wlan0: associated
Jan 30 23:46:05 zaphod wpa_supplicant[1381]: Associated with 02:1d:73:8e:de:98
Jan 30 23:46:05 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jan 30 23:46:06 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jan 30 23:46:06 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jan 30 23:46:07 zaphod kernel: [16583.594707] iwlagn 0000:0b:00.0: iwl_tx_agg_start on ra = 02:1d:73:8e:de:98 tid = 0
Jan 30 23:46:07 zaphod wpa_supplicant[1381]: WPA: Key negotiation completed with 02:1d:73:8e:de:98 [PTK=CCMP GTK=CCMP]
Jan 30 23:46:07 zaphod wpa_supplicant[1381]: CTRL-EVENT-CONNECTED - Connection to 02:1d:73:8e:de:98 completed (reauth) [id=0 id_str=]
Jan 30 23:46:07 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jan 30 23:46:40 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS

---

### Post by zaphod777 on 2010-01-30
Connection just dropped again logs below:

Jan 30 23:54:40 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:55:08 zaphod kernel: [17125.132034] wlan0: deauthenticated from 02:1d:73:8e:de:98 (Reason: 6)
Jan 30 23:55:09 zaphod wpa_supplicant[1381]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan 30 23:55:09 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jan 30 23:55:09 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 30 23:55:10 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:55:17 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:55:24 zaphod NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Jan 30 23:55:24 zaphod NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Jan 30 23:55:24 zaphod NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 4435
Jan 30 23:55:24 zaphod NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jan 30 23:55:24 zaphod avahi-daemon[1097]: Withdrawing address record for 192.168.11.100 on wlan0.
Jan 30 23:55:24 zaphod avahi-daemon[1097]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.11.100.
Jan 30 23:55:24 zaphod avahi-daemon[1097]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) starting connection 'Auto 44'
Jan 30 23:55:24 zaphod NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 30 23:55:24 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 30 23:55:24 zaphod NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto 44' has security, but secrets are required.
Jan 30 23:55:24 zaphod NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 30 23:55:24 zaphod NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 30 23:55:24 zaphod NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 44' has security, and secrets exist.  No new secrets needed.
Jan 30 23:55:24 zaphod NetworkManager: <info>  Config: added 'ssid' value '44'
Jan 30 23:55:24 zaphod NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jan 30 23:55:24 zaphod NetworkManager: <info>  Config: added 'bssid' value '02:1d:73:8e:de:98'
Jan 30 23:55:24 zaphod NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jan 30 23:55:24 zaphod NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jan 30 23:55:24 zaphod NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 30 23:55:24 zaphod NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 30 23:55:24 zaphod NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 30 23:55:24 zaphod NetworkManager: <info>  Config: set interface ap_scan to 1
Jan 30 23:55:24 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:55:24 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 30 23:55:26 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:55:26 zaphod wpa_supplicant[1381]: WPS-AP-AVAILABLE 
Jan 30 23:55:26 zaphod wpa_supplicant[1381]: Trying to associate with 02:1d:73:8e:de:98 (SSID='44' freq=2457 MHz)
Jan 30 23:55:26 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 30 23:55:26 zaphod kernel: [17142.693456] wlan0: direct probe to AP 02:1d:73:8e:de:98 (try 1)
Jan 30 23:55:26 zaphod kernel: [17142.701297] wlan0: direct probe responded
Jan 30 23:55:26 zaphod kernel: [17142.701308] wlan0: authenticate with AP 02:1d:73:8e:de:98 (try 1)
Jan 30 23:55:26 zaphod kernel: [17142.712083] wlan0: authenticated
Jan 30 23:55:26 zaphod kernel: [17142.712135] wlan0: associate with AP 02:1d:73:8e:de:98 (try 1)
Jan 30 23:55:26 zaphod kernel: [17142.915606] wlan0: associate with AP 02:1d:73:8e:de:98 (try 2)
Jan 30 23:55:26 zaphod kernel: [17142.975360] wlan0: RX ReassocResp from 02:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan 30 23:55:26 zaphod kernel: [17142.975364] wlan0: associated
Jan 30 23:55:26 zaphod wpa_supplicant[1381]: Associated with 02:1d:73:8e:de:98
Jan 30 23:55:26 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jan 30 23:55:28 zaphod kernel: [17144.751463] wlan0: deauthenticated from 02:1d:73:8e:de:98 (Reason: 2)
Jan 30 23:55:28 zaphod wpa_supplicant[1381]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan 30 23:55:28 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Jan 30 23:55:28 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 30 23:55:28 zaphod wpa_supplicant[1381]: CTRL-EVENT-SCAN-RESULTS 
Jan 30 23:55:28 zaphod wpa_supplicant[1381]: WPS-AP-AVAILABLE 
Jan 30 23:55:28 zaphod wpa_supplicant[1381]: Trying to associate with 02:1d:73:8e:de:98 (SSID='44' freq=2457 MHz)
Jan 30 23:55:28 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 30 23:55:28 zaphod kernel: [17144.930669] wlan0: direct probe to AP 02:1d:73:8e:de:98 (try 1)
Jan 30 23:55:28 zaphod kernel: [17144.962363] wlan0: direct probe responded
Jan 30 23:55:28 zaphod kernel: [17144.962375] wlan0: authenticate with AP 02:1d:73:8e:de:98 (try 1)
Jan 30 23:55:28 zaphod kernel: [17145.015336] wlan0: authenticated
Jan 30 23:55:28 zaphod kernel: [17145.015393] wlan0: associate with AP 02:1d:73:8e:de:98 (try 1)
Jan 30 23:55:28 zaphod kernel: [17145.019476] wlan0: RX ReassocResp from 02:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan 30 23:55:28 zaphod kernel: [17145.019485] wlan0: associated
Jan 30 23:55:28 zaphod wpa_supplicant[1381]: Associated with 02:1d:73:8e:de:98
Jan 30 23:55:28 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jan 30 23:55:30 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jan 30 23:55:30 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jan 30 23:55:30 zaphod wpa_supplicant[1381]: WPA: Key negotiation completed with 02:1d:73:8e:de:98 [PTK=CCMP GTK=CCMP]
Jan 30 23:55:30 zaphod wpa_supplicant[1381]: CTRL-EVENT-CONNECTED - Connection to 02:1d:73:8e:de:98 completed (reauth) [id=0 id_str=]
Jan 30 23:55:30 zaphod NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jan 30 23:55:30 zaphod NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '44'.
Jan 30 23:55:30 zaphod NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 30 23:55:30 zaphod NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 30 23:55:30 zaphod NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jan 30 23:55:30 zaphod NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 30 23:55:31 zaphod NetworkManager: <info>  dhclient started with pid 5325
Jan 30 23:55:31 zaphod NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 30 23:55:31 zaphod NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 30 23:55:31 zaphod NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 30 23:55:31 zaphod NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 30 23:55:31 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan 30 23:55:31 zaphod dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan 30 23:55:31 zaphod dhclient: All rights reserved.
Jan 30 23:55:31 zaphod dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan 30 23:55:31 zaphod dhclient: 
Jan 30 23:55:31 zaphod NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jan 30 23:55:31 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan 30 23:55:31 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan 30 23:55:31 zaphod dhclient: Sending on   Socket/fallback
Jan 30 23:55:34 zaphod dhclient: DHCPREQUEST of 192.168.11.100 on wlan0 to 255.255.255.255 port 67
Jan 30 23:55:34 zaphod dhclient: DHCPACK of 192.168.11.100 from 192.168.11.1
Jan 30 23:55:34 zaphod dhclient: bound to 192.168.11.100 -- renewal in 66384 seconds.
Jan 30 23:55:34 zaphod NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Jan 30 23:55:34 zaphod NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 30 23:55:34 zaphod NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 30 23:55:34 zaphod NetworkManager: <info>    address 192.168.11.100
Jan 30 23:55:34 zaphod NetworkManager: <info>    prefix 24 (255.255.255.0)
Jan 30 23:55:34 zaphod NetworkManager: <info>    gateway 192.168.11.1
Jan 30 23:55:34 zaphod NetworkManager: <info>    nameserver '192.168.11.1'
Jan 30 23:55:34 zaphod NetworkManager: <info>    domain name 'chgsk1.kt.home.ne.jp'
Jan 30 23:55:34 zaphod NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 30 23:55:34 zaphod NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 30 23:55:34 zaphod NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan 30 23:55:34 zaphod avahi-daemon[1097]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.11.100.
Jan 30 23:55:34 zaphod avahi-daemon[1097]: New relevant interface wlan0.IPv4 for mDNS.
Jan 30 23:55:34 zaphod avahi-daemon[1097]: Registering new address record for 192.168.11.100 on wlan0.IPv4.
Jan 30 23:55:35 zaphod NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jan 30 23:55:35 zaphod NetworkManager: <info>  Policy set 'Auto 44' (wlan0) as default for routing and DNS.
Jan 30 23:55:35 zaphod NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jan 30 23:55:35 zaphod NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 30 23:55:36 zaphod kernel: [17152.828657] iwlagn 0000:0b:00.0: iwl_tx_agg_start on ra = 02:1d:73:8e:de:98 tid = 0
Jan 30 23:55:37 zaphod ntpdate[5371]: adjust time server 91.189.94.4 offset -0.000369 sec

---

### Post by jfernyhough on 2010-01-30
In your logs there's a Disassociation Reason 2, which means incorrect credentials. It's not a WPA2-Enterprise setup is it?

Is there anything in dmesg about deprecated firmware? There are two versions, -1 and -2. My card has played up in the past when it couldn't find the -2 version (a missing symlink in /lib/firmware IIRC).

Occasionally network manager stops working and I've found the easiest way to fix things is to delete the connection from nm-applet and put the settings in again.

---

### Post by zaphod777 on 2010-01-30
No it's not a corporate WPA just running of my home router.

I have tried removing and adding the network again but it doesn't really help.

I have attached the dmesg log files. I don't see anything there but maybe you can see something I can't.

---

### Post by Jay_Bee on 2010-01-31
I had the same issue when I used Transmission BitTorrent Client, but since I moved to Deluge I no longer get disconnected. Maybe it's just a coincidance, but I suggest you give it a try and see for yourself.

---

### Post by zaphod777 on 2010-01-31
I have actually been using Deluge for a while. I think it has something to do with Network Manager getting a result back from the driver that it didn't expect from my reading.

Anyone have a wireless N network card they would recommend? I need a mini pci card that will fit in a Dell XPS 1530 laptop.

---

### Post by Seventh Reign on 2010-01-31
This was a big problem for Karmic when it was first released.   It seems to have been fixed lately tho.  I guess its back in Lucid.  I hope they fix it BEFORE the final release in April this time.

As for Transmission .. talk about 1 step forward and 10 steps back.  There is something seriously wrong with it lately.  Its as buggy and useless as KDE 4.0 was.

---

### Post by zaphod777 on 2010-02-06
Well after trying basicly everything even 10.4 beta. I Re-installed 9.04 then upgraded to 9.10 and it seams to work perfect. There seams to be some issue with the current drivers.

---

### Post by zaphod777 on 2010-02-06
If anyone can help me find what is different I would like to find out so we can get a fix into 10.04 many people are having this issue.

Not sure if it makes a difference but this time I opted for ext3 and no home drive encryption.

---

### Post by zilvia on 2010-02-26
I switched to wicd instead of network manager and it seems to work pretty well.
Guess it's a network manager bug, involving the authentication phase.
When the wlan is very busy, it kinda "forgets" the WPA key.
zil

---

