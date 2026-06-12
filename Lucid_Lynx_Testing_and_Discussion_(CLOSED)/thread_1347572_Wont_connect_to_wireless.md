---
title: "Wont connect to wireless"
date: 2009-12-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by descendent87 on 2009-12-06
Installed the lucid daily image, everything wen't ok but network manager won't connect to my wireless. It see's the network and I put in the wep key but then the icon just keeps spinning and the "Wireless Network Authentication Required" box pops up I put the key in again and the same thing happens. Never connects.

This is some of the info in system log when I try to connect with DHCP
```
Dec  6 16:33:23 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:33:23 ubuntu kernel: [  157.161329] wlan0: direct probe to AP 00:1c:df:83:43:c9 (try 1)
Dec  6 16:33:23 ubuntu kernel: [  157.166622] wlan0: direct probe responded
Dec  6 16:33:23 ubuntu kernel: [  157.166634] wlan0: authenticate with AP 00:1c:df:83:43:c9 (try 1)
Dec  6 16:33:23 ubuntu kernel: [  157.175814] wlan0: authenticated
Dec  6 16:33:23 ubuntu kernel: [  157.175853] wlan0: associate with AP 00:1c:df:83:43:c9 (try 1)
Dec  6 16:33:23 ubuntu wpa_supplicant[1143]: Associated with 00:1c:df:83:43:c9
Dec  6 16:33:23 ubuntu wpa_supplicant[1143]: CTRL-EVENT-CONNECTED - Connection to 00:1c:df:83:43:c9 completed (reauth) [id=0 id_str=]
Dec  6 16:33:23 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Dec  6 16:33:23 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Dec  6 16:33:23 ubuntu NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Belkin54g'.
Dec  6 16:33:23 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec  6 16:33:23 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec  6 16:33:23 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Dec  6 16:33:23 ubuntu NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Dec  6 16:33:23 ubuntu NetworkManager: <info>  dhclient started with pid 1786
Dec  6 16:33:23 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Dec  6 16:33:23 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec  6 16:33:23 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Dec  6 16:33:23 ubuntu kernel: [  157.226249] wlan0: RX AssocResp from 00:1c:df:83:43:c9 (capab=0x431 status=0 aid=5)
Dec  6 16:33:23 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Dec  6 16:33:23 ubuntu kernel: [  157.226258] wlan0: associated
Dec  6 16:33:23 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.2
Dec  6 16:33:23 ubuntu dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec  6 16:33:23 ubuntu dhclient: All rights reserved.
Dec  6 16:33:23 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec  6 16:33:23 ubuntu dhclient: 
Dec  6 16:33:23 ubuntu NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Dec  6 16:33:23 ubuntu dhclient: Listening on LPF/wlan0/00:11:50:de:2a:c4
Dec  6 16:33:23 ubuntu dhclient: Sending on   LPF/wlan0/00:11:50:de:2a:c4
Dec  6 16:33:23 ubuntu dhclient: Sending on   Socket/fallback
Dec  6 16:33:27 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec  6 16:33:33 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Dec  6 16:33:33 ubuntu dhclient: DHCPOFFER of 192.168.2.3 from 192.168.2.1
Dec  6 16:33:33 ubuntu dhclient: DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67
Dec  6 16:33:39 ubuntu dhclient: DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67
Dec  6 16:33:53 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Dec  6 16:33:53 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:33:58 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec  6 16:34:04 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec  6 16:34:09 ubuntu NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Dec  6 16:34:09 ubuntu NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1786
Dec  6 16:34:09 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Dec  6 16:34:09 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Dec  6 16:34:09 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'Auto Belkin54g'.
Dec  6 16:34:09 ubuntu NetworkManager: <info>  (wlan0): device state change: 7 -> 6 (reason 0)
Dec  6 16:34:09 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Dec  6 16:34:09 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.

```

And this is using static IP address
```
Dec  6 16:41:09 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Belkin54g'
Dec  6 16:41:20 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  6 16:41:20 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Belkin54g' has security, but secrets are required.
Dec  6 16:41:20 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  6 16:41:20 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  6 16:41:20 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Belkin54g' has security, and secrets exist.  No new secrets needed.
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'Belkin54g'
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Dec  6 16:41:20 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  6 16:41:20 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  6 16:41:20 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
Dec  6 16:41:20 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Dec  6 16:41:20 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec  6 16:41:21 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:41:28 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:41:34 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:41:36 ubuntu NetworkManager: <info>  wlan0: link timed out.
Dec  6 16:41:41 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:41:47 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:41:53 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:42:00 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:42:06 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:42:13 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:42:19 ubuntu wpa_supplicant[1143]: CTRL-EVENT-SCAN-RESULTS 
Dec  6 16:42:21 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Dec  6 16:42:21 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Dec  6 16:42:21 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Dec  6 16:42:21 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected

```

---

### Post by descendent87 on 2009-12-08
Obviously has something to do with the .32 kernel as I've gone back to karmic and everything works fine, installed the .32 kernel to get 3D with the ATI drivers and had this problem again

---

### Post by Reiger on 2009-12-08
Well there has been a dhcp3-client update not too long ago. So try a upgrade on Lucid?

---

### Post by TKbuntu on 2009-12-09
I have the same experience.  Lucid daily live-cd, up to 3 Dec, wireless worked ok.  Since 5 Dec the daily live-cd will not connect.  Wireless setup does not use wep or wpa, so a less complex scenario.  In addition to the earlier lucid dailys 9.10, 9.04 etc. get a wireless connection, so it is not the hardware (pc or router)  Hopefully Alpha 1 will not have this issue.  Regards,  TK

---

### Post by descendent87 on 2009-12-10
> **Reiger said:**
> Well there has been a dhcp3-client update not too long ago. So try a upgrade on Lucid?

Tried updating everything yesterday and still no change, hoping it's fixed in alpha 1

---

### Post by descendent87 on 2009-12-10
Just installed alpha 1 and still no change, currently using a karmic live cd.

---

### Post by 00ber n00b on 2009-12-20
I'm having the same issue.  lucid doesn't even see my wireless card.

---

### Post by 00ber n00b on 2009-12-20
Well, I'm an idiot.  I googled the issue, and someone mentioned fn+f2 (whatever turns your wireless on) and it works perfectly.  lol

---

### Post by UbuWu on 2009-12-22
I am having the same issue, wireless worked fine in karmic but now I can't connect to my wireless network anymore. It still does connect to unencrypted networks though, although taking longer than usual. Did you file a bug about this that I can also subscribe to?

---

### Post by UbuWu on 2009-12-22
Descendent87, do you have a realtek wireless chip? If so you might be affected by this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093)

---

### Post by descendent87 on 2009-12-22
Yes I have a realtek rt61 chip, I'm currently on my arch linux install which has kernel 2.6.32 and exactly the same problem and the power off trick works fine at the moment

---

### Post by zengeos on 2009-12-22
Strange.

Wireless improvement was the FIRST thing I noticed. Connection is stronger and far more stable in Lucid than on either Jaunty or Karmic...nearly double the signal strength reported....from both of my routers, no less.

---

### Post by descendent87 on 2009-12-22
it's not an ubuntu problem, it's the .32 kernel and hopefully it'll be fixed soon. Once I am connected the signal is much stronger than usual aswell

---

### Post by Ibidem on 2010-01-09
I guess it's chipset-dependent--I have a good connection in Lucid.
Atheros AR5007, reported as AR5001, ath5k/WEP.
2.6.32 has been very nice for me.
Ibidem

---

