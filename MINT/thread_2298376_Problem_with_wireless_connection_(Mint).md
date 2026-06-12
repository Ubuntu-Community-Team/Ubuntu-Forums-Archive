---
title: "Problem with wireless connection (Mint)"
date: 2015-10-10
forum: MINT
---

### Post by luigi12 on 2015-10-10
Hi everybody! I've got a problem with Linux Mint: (I posted here because I've seen it's the same for Ubuntu)
I've got a WNA3100 adapter in my Desktop for Wireless connection. 
I've installed the bcmn43xx64 driver and it works: the usb is ok and can scan wireless.
But when I try to connect, it starts an "ask for password" loop.
I put the correct password, but can't connect. :icon_frown::icon_frown:

The syslog is: 

```
Oct 10 17:17:21 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): supplicant interface state: ready -> disconnected 
Oct 10 17:17:21 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0) supports 1 scan SSIDs
Oct 10 17:17:31 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) starting connection 'Connessione NETGEAR70 automatica'
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0/wireless): access point 'Connessione NETGEAR70 automatica' has security, but secrets are required.
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0/wireless): connection 'Connessione NETGEAR70 automatica' has security, and secrets exist.  No new secrets needed.
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Config: added 'ssid' value 'NETGEAR70'
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Config: added 'scan_ssid' value '1'
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
**Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Config: added 'psk' value '<omitted>'**
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 10 17:17:33 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Config: set interface ap_scan to 1
Oct 10 17:17:41 luigi-PA65-UD3-B3 wpa_supplicant[3854]: wlan0: Trying to associate with 20:4e:7f:c2:e9:26 (SSID='NETGEAR70' freq=2437 MHz)
Oct 10 17:17:41 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): supplicant interface state: inactive -> associating
Oct 10 17:17:42 luigi-PA65-UD3-B3 wpa_supplicant[3854]: wlan0: Associated with 20:4e:7f:c2:e9:26
Oct 10 17:17:42 luigi-PA65-UD3-B3 kernel: [ 3256.701918] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 10 17:17:42 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Oct 10 17:17:43 luigi-PA65-UD3-B3 avahi-daemon[1177]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::c63d:c7ff:fed0:ae5.
Oct 10 17:17:43 luigi-PA65-UD3-B3 avahi-daemon[1177]: New relevant interface wlan0.IPv6 for mDNS.
Oct 10 17:17:43 luigi-PA65-UD3-B3 avahi-daemon[1177]: Registering new address record for fe80::c63d:c7ff:fed0:ae5 on wlan0.*.
Oct 10 17:17:51 luigi-PA65-UD3-B3 wpa_supplicant[3854]: wlan0: CTRL-EVENT-DISCONNECTED bssid=20:4e:7f:c2:e9:26 reason=0
**Oct 10 17:17:51 luigi-PA65-UD3-B3 wpa_supplicant[3854]: wlan0: WPA: 4-Way Handshake failed - pre-shared key may be incorrect**
Oct 10 17:17:51 luigi-PA65-UD3-B3 wpa_supplicant[3854]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="NETGEAR70" auth_failures=1 duration=10
Oct 10 17:17:51 luigi-PA65-UD3-B3 wpa_supplicant[3854]: wlan0: Trying to associate with 20:4e:7f:c2:e9:26 (SSID='NETGEAR70' freq=2437 MHz)
Oct 10 17:17:51 luigi-PA65-UD3-B3 kernel: [ 3266.249949] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Oct 10 17:17:51 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): supplicant interface state: 4-way handshake -> associating
Oct 10 17:17:52 luigi-PA65-UD3-B3 wpa_supplicant[3854]: wlan0: Associated with 20:4e:7f:c2:e9:26
Oct 10 17:17:52 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Oct 10 17:17:58 luigi-PA65-UD3-B3 NetworkManager[1358]: <warn> Activation (wlan0/wireless): association took too long.
Oct 10 17:17:58 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Oct 10 17:17:58 luigi-PA65-UD3-B3 NetworkManager[1358]: <warn> Activation (wlan0/wireless): asking for new secrets
Oct 10 17:17:58 luigi-PA65-UD3-B3 wpa_supplicant[3854]: wlan0: CTRL-EVENT-DISCONNECTED bssid=20:4e:7f:c2:e9:26 reason=3 locally_generated=1
Oct 10 17:17:58 luigi-PA65-UD3-B3 wpa_supplicant[3854]: wlan0: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Oct 10 17:17:58 luigi-PA65-UD3-B3 wpa_supplicant[3854]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="NETGEAR70" auth_failures=2 duration=20
Oct 10 17:17:58 luigi-PA65-UD3-B3 NetworkManager[1358]: <warn> Connection disconnected (reason -3)
Oct 10 17:17:58 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Oct 10 17:17:58 luigi-PA65-UD3-B3 NetworkManager[1358]: <info> Activation (wlan0/wireless): disconnected during association, asking for new key.
Oct 10 17:17:58 luigi-PA65-UD3-B3 NetworkManager[1358]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
```

I don't understand why it puts the psk value to null.. I insert the password but it's always incorrect.
Thanks for your help!! :D:D:D

---

### Post by coffeecat on 2015-10-13
*Thread moved to the Linux Mint sub-forum.*

---

