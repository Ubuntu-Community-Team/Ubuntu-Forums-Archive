---
title: "Connect to WPA2-Enterprise wireless networks"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by linusr on 2010-04-14
I can connect to WPA2 perosnal networks but not WPA2 enterprise networks.
Laptop - Dell Vostro 1500 with Inter wireless card.

From logs,
> Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Corporate_WiFi' has security, and secrets exist.  No new secrets needed.
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Config: added 'ssid' value 'Corporate_WiFi'
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-EAP'
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Config: added 'password' value '<omitted>'
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Config: added 'eap' value 'PEAP'
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Config: added 'fragment_size' value '1300'
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Config: added 'phase2' value 'auth=MSCHAPV2'
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Config: added 'identity' value '***'
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Config: added 'anonymous_identity' value '*****'
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  Config: set interface ap_scan to 1
Apr 14 16:32:45 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Apr 14 16:32:48 DeepBlue wpa_supplicant[1106]: Trying to associate with 00:19:2f:32:36:e0 (SSID='Corporate_WiFi' freq=2462 MHz)
Apr 14 16:32:48 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 14 16:32:58 DeepBlue wpa_supplicant[1106]: Authentication with 00:19:2f:32:36:e0 timed out.
Apr 14 16:32:58 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr 14 16:32:58 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 14 16:33:01 DeepBlue wpa_supplicant[1106]: Trying to associate with 00:19:2f:32:36:e0 (SSID='Corporate_WiFi' freq=2462 MHz)
Apr 14 16:33:01 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 14 16:33:01 DeepBlue wpa_supplicant[1106]: Associated with 00:19:2f:32:36:e0
Apr 14 16:33:01 DeepBlue wpa_supplicant[1106]: CTRL-EVENT-EAP-STARTED EAP authentication started
Apr 14 16:33:01 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Apr 14 16:33:02 DeepBlue avahi-daemon[972]: Registering new address record for fe80::21b:77ff:fea8:6168 on wlan0.*.
Apr 14 16:33:10 DeepBlue wpa_supplicant[1106]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr 14 16:33:10 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Apr 14 16:33:10 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 14 16:33:13 DeepBlue wpa_supplicant[1106]: Trying to associate with 00:16:47:75:49:10 (SSID='Corporate_WiFi' freq=2412 MHz)
Apr 14 16:33:13 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 14 16:33:13 DeepBlue wpa_supplicant[1106]: Associated with 00:16:47:75:49:10
Apr 14 16:33:13 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Apr 14 16:33:14 DeepBlue wpa_supplicant[1106]: CTRL-EVENT-EAP-STARTED EAP authentication started
Apr 14 16:33:18 DeepBlue wpa_supplicant[1106]: CTRL-EVENT-EAP-STARTED EAP authentication started
Apr 14 16:33:18 DeepBlue wpa_supplicant[1106]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr 14 16:33:18 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Apr 14 16:33:18 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 14 16:33:21 DeepBlue wpa_supplicant[1106]: Trying to associate with 00:16:47:75:49:10 (SSID='Corporate_WiFi' freq=2412 MHz)
Apr 14 16:33:21 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 14 16:33:21 DeepBlue wpa_supplicant[1106]: Associated with 00:16:47:75:49:10
Apr 14 16:33:21 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Apr 14 16:33:21 DeepBlue wpa_supplicant[1106]: CTRL-EVENT-EAP-STARTED EAP authentication started
Apr 14 16:33:29 DeepBlue NetworkManager: <info>  wlan0: link timed out.
Apr 14 16:33:31 DeepBlue wpa_supplicant[1106]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr 14 16:33:31 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Apr 14 16:33:31 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 14 16:33:34 DeepBlue wpa_supplicant[1106]: Trying to associate with 00:17:94:d5:03:90 (SSID='Corporate_WiFi' freq=2437 MHz)
Apr 14 16:33:34 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 14 16:33:44 DeepBlue wpa_supplicant[1106]: Authentication with 00:17:94:d5:03:90 timed out.
Apr 14 16:33:44 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr 14 16:33:44 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 14 16:33:46 DeepBlue NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Apr 14 16:33:46 DeepBlue NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Apr 14 16:33:46 DeepBlue NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Apr 14 16:33:46 DeepBlue NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Apr 14 16:33:51 DeepBlue NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Apr 14 16:33:51 DeepBlue NetworkManager: <info>  Activation (wlan0) failed for access point (Corporate_WiFi)
Apr 14 16:33:51 DeepBlue NetworkManager: <info>  Marking connection 'Auto Corporate_WiFi' invalid.
Apr 14 16:33:51 DeepBlue NetworkManager: <info>  Activation (wlan0) failed.
Apr 14 16:33:51 DeepBlue NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Apr 14 16:33:51 DeepBlue NetworkManager: <info>  (wlan0): deactivating device (reason: 0).

any idea? thanks for d help

---

### Post by Reiger on 2010-04-14
Yes but you probably won't like it: try removing Network manager and installing WICD (sudo apt-get install wicd-gtk).

WICD has faaaaaar more connection templates than Network manager; or at least far more than I ever found out about. Plus, you can write your own if you need to. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by linusr on 2010-04-14
> **Reiger said:**
> Yes but you probably won't like it: try removing Network manager and installing WICD (sudo apt-get install wicd-gtk).

WICD has faaaaaar more connection templates than Network manager; or at least far more than I ever found out about. Plus, you can write your own if you need to. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

tried wicd... but had problem connecting to my home network as well.so removed wicd

is there a way using wpa_suppliant?

---

### Post by PGHammer on 2010-04-15
> **linusr said:**
> tried wicd... but had problem connecting to my home network as well.so removed wicd

is there a way using wpa_suppliant?

GNOME or KDE (Ubuntu or Kubuntu)?

I have *no* problems with WPA2 (Enterprise with AES+TKIP) in Kubuntu 10.04 (current beta); in fact, I've had no problems with WPA2 in Kubuntu since I changed to the current router (Netgear WNR-3500v1 which actually *requires* WPA2 Enterprise (AES+TKIP) due to the Comcast-supplied default configuration; this router was supplied via the Comcast Wireless Router Promotion of last year).  Is it possibly an adapter firmware issue?

---

### Post by linusr on 2010-04-15
> **PGHammer said:**
> GNOME or KDE (Ubuntu or Kubuntu)?

I have *no* problems with WPA2 (Enterprise with AES+TKIP) in Kubuntu 10.04 (current beta); in fact, I've had no problems with WPA2 in Kubuntu since I changed to the current router (Netgear WNR-3500v1 which actually *requires* WPA2 Enterprise (AES+TKIP) due to the Comcast-supplied default configuration; this router was supplied via the Comcast Wireless Router Promotion of last year).  Is it possibly an adapter firmware issue?

I'm on Gnome (Ubuntu). Not sure other Mac/Windows machines could easily connect to WPA2-enterprise but not Linux...

firmware, may not be the cause.. wpa2-personal networks works fine

---

