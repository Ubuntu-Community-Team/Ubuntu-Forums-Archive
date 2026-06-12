---
title: "regular loose wireless connection on karmic"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ahbart on 2009-09-15
Hello,
I have trouble with my wireless connection on Karmic. Once a twice a day I loose my connection. After that I'm not able to connect again. i have to reboot first. 
It does not happen to mu other computer on the same modem/router. So I think it has something to do with karmic. I did not have this problem on Jaunty. 

Can someone have look at my log files to see if there some reasson for disconnection in there?
Bart

syslog
```

Sep 15 12:58:27 readysteady kernel: [11494.968014] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 1 (-16).
Sep 15 12:58:31 readysteady kernel: [11499.148010] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Sep 15 12:58:33 readysteady wpa_supplicant[3437]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 15 12:58:33 readysteady kernel: [11501.148012] wlan0: no probe response from AP 00:1b:2f:3c:cc:c2 - disassociating
Sep 15 12:58:33 readysteady NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Sep 15 12:58:33 readysteady NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 15 12:58:35 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:58:41 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:58:47 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:58:49 readysteady NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Sep 15 12:58:49 readysteady NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Sep 15 12:58:49 readysteady NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Sep 15 12:58:49 readysteady NetworkManager: <info>  Activation (wlan0) starting connection 'Auto basonetwerk'
Sep 15 12:58:49 readysteady NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Sep 15 12:58:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 15 12:58:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 15 12:58:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 15 12:58:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 15 12:58:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 15 12:58:49 readysteady NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep 15 12:58:49 readysteady NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto basonetwerk' has security, and secrets exist.  No new secrets needed.
Sep 15 12:58:49 readysteady avahi-daemon[3433]: Withdrawing address record for 192.168.0.3 on wlan0.
Sep 15 12:58:49 readysteady NetworkManager: <info>  Config: added 'ssid' value 'basonetwerk'
Sep 15 12:58:49 readysteady avahi-daemon[3433]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.3.
Sep 15 12:58:49 readysteady NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep 15 12:58:49 readysteady NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Sep 15 12:58:49 readysteady NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Sep 15 12:58:49 readysteady avahi-daemon[3433]: Interface wlan0.IPv4 no longer relevant for mDNS.
Sep 15 12:58:49 readysteady NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 15 12:58:49 readysteady NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 15 12:58:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 15 12:58:49 readysteady NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Sep 15 12:58:49 readysteady NetworkManager: <info>  Config: set interface ap_scan to 1
Sep 15 12:58:49 readysteady nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Sep 15 12:58:52 readysteady NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 15 12:58:54 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:59:00 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:59:04 readysteady NetworkManager: <info>  wlan0: link timed out.
Sep 15 12:59:07 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:59:13 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:59:19 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:59:26 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:59:32 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:59:38 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:59:45 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto basonetwerk' has security, but secrets are required.
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto basonetwerk' has security, but secrets are required.
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto basonetwerk' has security, but secrets are required.
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto basonetwerk' has security, but secrets are required.
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 7)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) failed for access point (basonetwerk)
Sep 15 12:59:49 readysteady NetworkManager: <info>  Marking connection 'Auto basonetwerk' invalid.
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) failed.
Sep 15 12:59:49 readysteady NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Sep 15 12:59:49 readysteady NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Sep 15 13:00:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:02:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:04:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:06:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:08:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:09:01 readysteady /USR/SBIN/CRON[8470]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 15 13:10:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:12:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:14:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:16:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:17:02 readysteady /USR/SBIN/CRON[8501]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 15 13:18:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:20:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:22:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:24:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:26:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:28:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:30:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:32:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:34:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:35:44 readysteady avahi-daemon[3433]: Withdrawing address record for fe80::212:bfff:fe63:bad0 on wlan0.
Sep 15 13:35:55 readysteady kernel: [13742.665063] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 15 13:36:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 
Sep 15 13:40:27 readysteady wpa_supplicant[3437]: CTRL-EVENT-SCAN-RESULTS 

```

kern.log

```

Sep 15 12:58:27 readysteady kernel: [11494.968014] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 1 (-16).
Sep 15 12:58:31 readysteady kernel: [11499.148010] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Sep 15 12:58:33 readysteady kernel: [11501.148012] wlan0: no probe response from AP 00:1b:2f:3c:cc:c2 - disassociating

```

---

### Post by ahbart on 2009-09-15
In addition:
lsusb
```
Bus 001 Device 008: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi
```

---

### Post by overdrank on 2009-09-15
Moved to Karmic Koala Testing and Discussion

---

### Post by hanzomon4 on 2009-09-15
[Bug report]("https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/404433")

---

### Post by ahbart on 2009-09-16
> **hanzomon4 said:**
> [Bug report]("https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/404433")

I'm not a linux guru, so I do not understand this well. What part of my log files make you think this problem is associated to the launchpad bug you mention?

My pc is connected to a wpa-psk network. The rest of the day the connection is stable.

---

### Post by hanzomon4 on 2009-09-16
I had the exact same issue.. much less with wpa-psk but it still happened adding ```
force-hpet pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1
``` to the defoptions in /etc/grub.conf fixed the problem for the most part

---

### Post by ahbart on 2009-09-16
Thanks for your answer.
This morning I had another problem with Karmic. It was the 5th time I had to do a fsck on root (ext4) without a reason in my opinion. 
This morning it was even worse. I could not manage to start x anymore. 
Karmic is still to buggy in my opinion. They have a lot to do in one month.
I'm going back to Jaunty for now. Jaunty was very stable.

---

