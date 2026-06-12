---
title: "Intrepid - 802.1x PEAP authentication"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Haldo on 2008-10-22
Hello to everyone; I'm quite desperate about this issue, because I tried a lot of different solutions, which of course are not working.

In the institute where I do research there is a network (both wired and wireless) with an 802.1x authentication.
Parameters for the network are the following:

Method: 802.1x
Authentication: PEAP
Inner authentication: MSCHAPv2

These parameters are the same for both wired and wireless networks, and both networks use DHCP.
Before switching to ubuntu I was using Kubuntu, but I was not able to authenticate; I tried a live version of Ubuntu Hardy and the authentication was working, so I tried to install Ubuntu Intrepid, and now the authentication is not working any more.

I googled for days, tried all different solutions, but nothing works. The error is the same for both wired and wireless network: "Activation (eth0/wired): association took too long."
If I try to connect to the wired network disabling the authentication, then I can connect (I receive a valid IP and so on), but a lot of things don't work (such as ssh). Wireless doesn't work anyway.
A friend of mine with Ubuntu Hardy can authenticate to the wired network (same configuration) but not to the wireless.

Some things I tried:
- disable ipv6 from the file /etc/modprobe.d/aliases
- added options cfg80211 ieee80211_regdom=EU in the file /etc/modprobe.d/options (too see if the wireless could work)
- when I was using Kubuntu I even tried the manual configuration of wpasupplicant

In the log you will see the name "CAMPUSIMT\" before my username; that is correct, I have to use that full username even when logging to the proxy.
Some data (ask me wathever you want):

daemon.log:
> Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) starting connection 'CAMPUSIMT' 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0/wired): connection 'CAMPUSIMT' has security, but secrets are required. 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  (eth0): device state change: 5 -> 6 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 22 16:16:49 alex-acer nm-system-settings: add_secrets: unhandled secret private-key type GArray_guchar_
Oct 22 16:16:49 alex-acer nm-system-settings: add_secrets: unhandled secret phase2-private-key type GArray_guchar_
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  (eth0): device state change: 6 -> 4 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0/wired): connection 'CAMPUSIMT' requires no security. No secrets needed. 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  (eth0) supplicant interface is now in state 2 (from 1). 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Config: added 'password' value '<omitted>' 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Config: added 'key_mgmt' value 'IEEE8021X' 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Config: added 'eapol_flags' value '0' 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Config: added 'eap' value 'PEAP' 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Config: added 'fragment_size' value '1300' 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Config: added 'phase1' value 'peapver=1' 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Config: added 'phase2' value 'auth=MSCHAPV2' 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Config: added 'identity' value 'CAMPUSIMT\myUserName' 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  Config: set interface ap_scan to 1 
Oct 22 16:16:49 alex-acer NetworkManager: <info>  (eth0) Supplicant interface state change: 0 -> 4 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Activation (eth0/wired): association took too long. 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  (eth0): device state change: 5 -> 6 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Activation (eth0/wired): asking for new secrets 
Oct 22 16:17:14 alex-acer nm-system-settings: add_secrets: unhandled secret private-key type GArray_guchar_
Oct 22 16:17:14 alex-acer nm-system-settings: add_secrets: unhandled secret phase2-private-key type GArray_guchar_
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  (eth0): device state change: 6 -> 4 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Activation (eth0/wired): connection 'CAMPUSIMT' requires no security. No secrets needed. 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  (eth0) supplicant interface is now in state 2 (from 1). 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Config: added 'password' value '<omitted>' 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Config: added 'key_mgmt' value 'IEEE8021X' 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Config: added 'eapol_flags' value '0' 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Config: added 'eap' value 'PEAP' 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Config: added 'fragment_size' value '1300' 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Config: added 'phase1' value 'peapver=1' 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Config: added 'phase2' value 'auth=MSCHAPV2' 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Config: added 'identity' value 'CAMPUSIMT\myUserName' 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  Config: set interface ap_scan to 1 
Oct 22 16:17:14 alex-acer NetworkManager: <info>  (eth0) Supplicant interface state change: 0 -> 4 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Activation (eth0/wired): association took too long. 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  (eth0): device state change: 5 -> 6 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Activation (eth0/wired): asking for new secrets 
Oct 22 16:17:39 alex-acer nm-system-settings: add_secrets: unhandled secret private-key type GArray_guchar_
Oct 22 16:17:39 alex-acer nm-system-settings: add_secrets: unhandled secret phase2-private-key type GArray_guchar_
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  (eth0): device state change: 6 -> 4 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Activation (eth0/wired): connection 'CAMPUSIMT' requires no security. No secrets needed. 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  (eth0) supplicant interface is now in state 2 (from 1). 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Config: added 'password' value '<omitted>' 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Config: added 'key_mgmt' value 'IEEE8021X' 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Config: added 'eapol_flags' value '0' 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Config: added 'eap' value 'PEAP' 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Config: added 'fragment_size' value '1300' 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Config: added 'phase1' value 'peapver=1' 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Config: added 'phase2' value 'auth=MSCHAPV2' 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Config: added 'identity' value 'CAMPUSIMT\myUserName' 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  Config: set interface ap_scan to 1 
Oct 22 16:17:39 alex-acer NetworkManager: <info>  (eth0) Supplicant interface state change: 0 -> 4 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Activation (eth0/wired): association took too long. 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  (eth0): device state change: 5 -> 6 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Activation (eth0/wired): asking for new secrets 
Oct 22 16:18:04 alex-acer nm-system-settings: add_secrets: unhandled secret private-key type GArray_guchar_
Oct 22 16:18:04 alex-acer nm-system-settings: add_secrets: unhandled secret phase2-private-key type GArray_guchar_
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  (eth0): device state change: 6 -> 4 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Activation (eth0/wired): connection 'CAMPUSIMT' requires no security. No secrets needed. 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  (eth0) supplicant interface is now in state 2 (from 1). 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Config: added 'password' value '<omitted>' 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Config: added 'key_mgmt' value 'IEEE8021X' 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Config: added 'eapol_flags' value '0' 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Config: added 'eap' value 'PEAP' 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Config: added 'fragment_size' value '1300' 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Config: added 'phase1' value 'peapver=1' 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Config: added 'phase2' value 'auth=MSCHAPV2' 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Config: added 'identity' value 'CAMPUSIMT\myUserName' 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  Config: set interface ap_scan to 1 
Oct 22 16:18:04 alex-acer NetworkManager: <info>  (eth0) Supplicant interface state change: 0 -> 4 
Oct 22 16:18:29 alex-acer NetworkManager: <info>  Activation (eth0/wired): association took too long. 
Oct 22 16:18:29 alex-acer NetworkManager: <info>  (eth0): device state change: 5 -> 9 
Oct 22 16:18:29 alex-acer NetworkManager: <info>  Marking connection 'CAMPUSIMT' invalid. 
Oct 22 16:18:29 alex-acer NetworkManager: <info>  Activation (eth0) failed. 
Oct 22 16:18:29 alex-acer NetworkManager: <info>  (eth0): device state change: 9 -> 3 
Oct 22 16:18:29 alex-acer NetworkManager: <info>  (eth0): deactivating device (reason: 0). 


lspci -vv
> 02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 011c
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 219
	Region 0: Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1001
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 218
	Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945


Thank you very much for the support.

---

