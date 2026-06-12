---
title: "Wireless does not work with WPA-Encryption, iwl4965"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Teamgeist on 2008-10-17
Hi.

In Intrepid my wireless doesn't work with WPA encryption.
It's an Intel 4965 Chip. Firmware is loaded and card recognized.

The circle just spins forever and then asks for the WPA-key.
When I enter the key. The thing spins again but is unable to connect.


here an excerpt from /var/log/syslog:

```
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) starting connection 'Auto ubuntulinux' 
Oct 17 14:08:41 m1330 NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 17 14:08:41 m1330 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto ubuntulinux' has security, but secrets are required. 
Oct 17 14:08:41 m1330 NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 17 14:08:41 m1330 NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 17 14:08:41 m1330 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto ubuntulinux' has security, and secrets exist.  No new secrets needed. 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Config: added 'ssid' value 'ubuntulinux' 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 17 14:08:41 m1330 NetworkManager: <info>  Config: set interface ap_scan to 1 
Oct 17 14:08:41 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 1 -> 2 
```

snip

```
Oct 17 14:08:42 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Oct 17 14:08:42 m1330 kernel: [   72.301605] wlan0: authenticate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:08:42 m1330 kernel: [   72.303231] wlan0: authenticated
Oct 17 14:08:42 m1330 kernel: [   72.303244] wlan0: associate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:08:42 m1330 kernel: [   72.307294] wlan0: RX AssocResp from 00:0f:3d:9e:ed:7a (capab=0x471 status=0 aid=1)
Oct 17 14:08:42 m1330 kernel: [   72.307306] wlan0: associated
Oct 17 14:08:42 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 5 
Oct 17 14:08:42 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 4 
Oct 17 14:08:44 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Oct 17 14:08:50 m1330 kernel: [   80.314616] wlan0: deauthenticated
Oct 17 14:08:50 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 0 
Oct 17 14:08:50 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Oct 17 14:08:51 m1330 kernel: [   81.312182] wlan0: authenticate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:08:51 m1330 kernel: [   81.313762] wlan0: authenticated
Oct 17 14:08:51 m1330 kernel: [   81.313773] wlan0: associate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:08:51 m1330 kernel: [   81.317285] wlan0: RX ReassocResp from 00:0f:3d:9e:ed:7a (capab=0x471 status=0 aid=1)
Oct 17 14:08:51 m1330 kernel: [   81.317296] wlan0: associated
Oct 17 14:08:51 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Oct 17 14:08:51 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Oct 17 14:08:59 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 0 
Oct 17 14:08:59 m1330 kernel: [   89.317959] wlan0: deauthenticated
Oct 17 14:08:59 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Oct 17 14:09:00 m1330 kernel: [   90.320078] wlan0: authenticate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:09:00 m1330 kernel: [   90.322237] wlan0: authenticated
Oct 17 14:09:00 m1330 kernel: [   90.322251] wlan0: associate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:09:00 m1330 kernel: [   90.325666] wlan0: RX ReassocResp from 00:0f:3d:9e:ed:7a (capab=0x471 status=0 aid=1)
Oct 17 14:09:00 m1330 kernel: [   90.325678] wlan0: associated
Oct 17 14:09:00 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 5 
Oct 17 14:09:00 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 4 
Oct 17 14:09:01 m1330 kernel: [   91.324631] NET: Registered protocol family 10
Oct 17 14:09:01 m1330 kernel: [   91.327042] lo: Disabled Privacy Extensions
Oct 17 14:09:02 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Oct 17 14:09:02 m1330 avahi-daemon[5056]: Registering new address record for fe80::21d:9ff:fe3f:546c on eth0.*.
Oct 17 14:09:02 m1330 avahi-daemon[5056]: Registering new address record for fe80::21f:3bff:fe61:d791 on wlan0.*.
Oct 17 14:09:05 m1330 NetworkManager: <info>  wlan0: link timed out. 
Oct 17 14:09:06 m1330 kernel: [   96.396877] wlan0: disassociating by local choice (reason=3)
Oct 17 14:09:06 m1330 NetworkManager: <info>  Activation (wlan0/wireless): association took too long. 
Oct 17 14:09:06 m1330 NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Oct 17 14:09:06 m1330 NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Oct 17 14:09:06 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 0 
Oct 17 14:09:09 m1330 NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Oct 17 14:09:09 m1330 NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) failed for access point (ubuntulinux) 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Marking connection 'Auto ubuntulinux' invalid. 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) failed. 
Oct 17 14:09:09 m1330 NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Oct 17 14:09:09 m1330 NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) starting connection 'Auto ubuntulinux' 
Oct 17 14:09:09 m1330 NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 17 14:09:09 m1330 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto ubuntulinux' has security, but secrets are required. 
Oct 17 14:09:09 m1330 NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 17 14:09:09 m1330 NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 17 14:09:09 m1330 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto ubuntulinux' has security, and secrets exist.  No new secrets needed. 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Config: added 'ssid' value 'ubuntulinux' 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 17 14:09:09 m1330 NetworkManager: <info>  Config: set interface ap_scan to 1 
Oct 17 14:09:09 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Oct 17 14:09:10 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Oct 17 14:09:10 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Oct 17 14:09:10 m1330 kernel: [  100.565954] wlan0: authenticate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:09:10 m1330 kernel: [  100.567528] wlan0: authenticated
Oct 17 14:09:10 m1330 kernel: [  100.567539] wlan0: associate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:09:10 m1330 kernel: [  100.570400] wlan0: RX AssocResp from 00:0f:3d:9e:ed:7a (capab=0x471 status=0 aid=1)
Oct 17 14:09:10 m1330 kernel: [  100.570409] wlan0: associated
Oct 17 14:09:10 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 4 
Oct 17 14:09:10 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Oct 17 14:09:11 m1330 kernel: [  101.697057] eth0: no IPv6 routers present
Oct 17 14:09:11 m1330 kernel: [  101.877024] wlan0: no IPv6 routers present
Oct 17 14:09:18 m1330 kernel: [  108.575916] wlan0: deauthenticated
Oct 17 14:09:18 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 0 
Oct 17 14:09:18 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Oct 17 14:09:19 m1330 kernel: [  109.572201] wlan0: authenticate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:09:19 m1330 kernel: [  109.573785] wlan0: authenticated
Oct 17 14:09:19 m1330 kernel: [  109.573794] wlan0: associate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:09:19 m1330 kernel: [  109.576781] wlan0: RX ReassocResp from 00:0f:3d:9e:ed:7a (capab=0x471 status=0 aid=1)
Oct 17 14:09:19 m1330 kernel: [  109.576791] wlan0: associated
Oct 17 14:09:19 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Oct 17 14:09:19 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Oct 17 14:09:25 m1330 NetworkManager: <info>  wlan0: link timed out. 
Oct 17 14:09:27 m1330 kernel: [  117.580132] wlan0: deauthenticated
Oct 17 14:09:27 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 0 
Oct 17 14:09:27 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Oct 17 14:09:28 m1330 kernel: [  118.580209] wlan0: authenticate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:09:28 m1330 kernel: [  118.581790] wlan0: authenticated
Oct 17 14:09:28 m1330 kernel: [  118.581804] wlan0: associate with AP 00:0f:3d:9e:ed:7a
Oct 17 14:09:28 m1330 kernel: [  118.584712] wlan0: RX ReassocResp from 00:0f:3d:9e:ed:7a (capab=0x471 status=0 aid=1)
Oct 17 14:09:28 m1330 kernel: [  118.584723] wlan0: associated
Oct 17 14:09:28 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 5 
Oct 17 14:09:28 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 4 
Oct 17 14:09:30 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Oct 17 14:09:34 m1330 kernel: [  124.236775] wlan0: disassociating by local choice (reason=3)
Oct 17 14:09:34 m1330 NetworkManager: <info>  Activation (wlan0/wireless): association took too long. 
Oct 17 14:09:34 m1330 NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Oct 17 14:09:34 m1330 NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Oct 17 14:09:34 m1330 NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 0 
Oct 17 14:09:38 m1330 NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Oct 17 14:09:38 m1330 NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Oct 17 14:09:38 m1330 NetworkManager: <info>  Activation (wlan0) failed for access point (ubuntulinux) 
Oct 17 14:09:38 m1330 NetworkManager: <info>  Marking connection 'Auto ubuntulinux' invalid. 
Oct 17 14:09:38 m1330 NetworkManager: <info>  Activation (wlan0) failed. 
Oct 17 14:09:38 m1330 NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Oct 17 14:09:38 m1330 NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
```

Any Ideas? Wired connection works just fine.

---

### Post by sdowney717 on 2008-10-17
use wep

---

### Post by Teamgeist on 2008-10-17
> **sdowney717 said:**
> use wep

Come on, it's 2008. ;)

---

### Post by sdowney717 on 2008-10-17
I never got wpa working in Hardy. wep worked fine.
even wpa can be broken. to me wireless security is simply a deterrent that a few persistent people might try to break but most dont bother to try.

[https://launchpad.net/ubuntu/intrepid/lpia/wpasupplicant](https://launchpad.net/ubuntu/intrepid/lpia/wpasupplicant)

do you have the latest wpa supplicant?

can you verify your wireless can connect to another OS or PC?

---

### Post by Teamgeist on 2008-10-19
Bug report here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963)

---

### Post by Teamgeist on 2008-10-22
Has anybody made any progress with this?

---

### Post by jfernyhough on 2008-10-22
Have you tried a setting a different WPA key? I had problems with certain characters (parentheses) on Kubuntu a few weeks ago, but a different key worked fine.

Also remove the connection from network manager (Right-click, edit connections...), then connect again. You might also remove the secrets for the connection from Passwords and Encryption Keys (seahorse) to make sure it asks for a new key.

As a last resort, I've found rebooting the wireless router/access point can inexplicably make it start working again.

---

### Post by Suzan on 2008-10-22
Does your WLAN use channel 12 or 13?

If yes, try a channel between 1-11 and try again.

---

### Post by Teamgeist on 2008-10-22
> **Suzan said:**
> Does your WLAN use channel 12 or 13?

If yes, try a channel between 1-11 and try again.

Hi Suzan.
Nope, after I saw this issue on ubuntuusers.de I checked and the router is on channel 10.

So this should not be a problem.

Maybe I will just re-install when the RC is out tomorrow...

---

### Post by OSConvert on 2008-10-26
I had reverted to 7.10 to make WPA work.  When I went to 8.04 WEP would work but not WPA.  The bug fix site noted on this page mentions solutions by ensuring that the wifi is on, and changing the password on the AP; but these seem to be red-herrings if the problem can be fixed by reverting to 7.10.

I was hoping that 8.10 would fix the problem, but it does not look hopeful.

---

### Post by Casey on 2008-10-26
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

I haven't tried WPA but WPA2 works perfectly for me with this card.  Is there any way you can try WPA2?

---

