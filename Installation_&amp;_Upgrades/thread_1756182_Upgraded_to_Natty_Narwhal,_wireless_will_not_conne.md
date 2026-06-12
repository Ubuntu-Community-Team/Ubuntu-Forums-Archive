---
title: "Upgraded to Natty Narwhal, wireless will not connect, but can still see networks?"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by omega128 on 2011-05-11
I just upgraded my desktop to 11.04, and the internet stopped working.

It's a 2.11 gigahertz desktop. There is no wired connection. For wireless, I am using a Ralink wireless USB. It worked perfectly in 10.10. To all appearances, the wireless works fine out of the box, without the need for extra drivers.

In Narwhal, it can still see the local networks, and when asked to, seems to be connecting to them, However, it refuses to actually finish any connection, and stops for seemingly no reason.

Logs, both on the router and in /var/log/syslog, show that the network card is talking to the router, and the router to the network card. But for some reason, the computer never accepts the offered IP address. It keeps timing out, even as the new IP address is staring it in the face.

After spending six hours trying to fix it, I started over with a fresh install. While installing, the wireless succesfully connected to the internet, and downloaded files (!). When I started the system up, it couldn't connect again.

It does the same thing with any network, with or without security enabled. I'm sure the answer is staring me in the face, but I cannot figure out why a card that worked in 10.10, and still works in the 11.04 setup, doesn't work with a fully installed system!

Can anyone help? :-(

The device, as listed in lsusb,
```
Bus 002 Device 002: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
```And this is what it says in /var/log/syslog,
```
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) starting connection 'Auto Narnia'
May 11 20:46:50 Jinn NetworkManager[870]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 11 20:46:50 Jinn NetworkManager[870]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0/wireless): access point 'Auto Narnia' has security, but secrets are required.
May 11 20:46:50 Jinn NetworkManager[870]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 11 20:46:50 Jinn NetworkManager[870]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 11 20:46:50 Jinn NetworkManager[870]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0/wireless): connection 'Auto Narnia' has security, and secrets exist.  No new secrets needed.
May 11 20:46:50 Jinn NetworkManager[870]: <info> Config: added 'ssid' value 'Narnia'
May 11 20:46:50 Jinn NetworkManager[870]: <info> Config: added 'scan_ssid' value '1'
May 11 20:46:50 Jinn NetworkManager[870]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 11 20:46:50 Jinn NetworkManager[870]: <info> Config: added 'psk' value '<omitted>'
May 11 20:46:50 Jinn NetworkManager[870]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 11 20:46:50 Jinn NetworkManager[870]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 11 20:46:50 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 11 20:46:50 Jinn NetworkManager[870]: <info> Config: set interface ap_scan to 1
May 11 20:46:50 Jinn NetworkManager[870]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
May 11 20:46:55 Jinn wpa_supplicant[1196]: Trying to associate with 94:44:52:11:98:8b (SSID='Narnia' freq=2412 MHz)
May 11 20:46:55 Jinn NetworkManager[870]: <info> (wlan0): supplicant connection state:  scanning -> associating
May 11 20:46:57 Jinn kernel: [ 4839.015285] wlan0: authenticate with 94:44:52:11:98:8b (try 1)
May 11 20:46:57 Jinn kernel: [ 4839.019438] wlan0: authenticated
May 11 20:46:59 Jinn kernel: [ 4841.016785] wlan0: associate with 94:44:52:11:98:8b (try 1)
May 11 20:46:59 Jinn kernel: [ 4841.023421] wlan0: RX AssocResp from 94:44:52:11:98:8b (capab=0x411 status=0 aid=1)
May 11 20:46:59 Jinn kernel: [ 4841.023426] wlan0: associated
May 11 20:46:59 Jinn wpa_supplicant[1196]: Associated with 94:44:52:11:98:8b
May 11 20:46:59 Jinn NetworkManager[870]: <info> (wlan0): supplicant connection state:  associating -> associated
May 11 20:46:59 Jinn NetworkManager[870]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
May 11 20:46:59 Jinn NetworkManager[870]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
May 11 20:46:59 Jinn wpa_supplicant[1196]: WPA: Key negotiation completed with 94:44:52:11:98:8b [PTK=CCMP GTK=CCMP]
May 11 20:46:59 Jinn wpa_supplicant[1196]: CTRL-EVENT-CONNECTED - Connection to 94:44:52:11:98:8b completed (reauth) [id=0 id_str=]
May 11 20:46:59 Jinn NetworkManager[870]: <info> (wlan0): supplicant connection state:  group handshake -> completed
May 11 20:46:59 Jinn NetworkManager[870]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Narnia'.
May 11 20:46:59 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
May 11 20:46:59 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
May 11 20:46:59 Jinn NetworkManager[870]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
May 11 20:46:59 Jinn NetworkManager[870]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 11 20:46:59 Jinn NetworkManager[870]: <info> dhclient started with pid 3098
May 11 20:46:59 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May 11 20:46:59 Jinn dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
May 11 20:46:59 Jinn dhclient: Copyright 2004-2010 Internet Systems Consortium.
May 11 20:46:59 Jinn dhclient: All rights reserved.
May 11 20:46:59 Jinn dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 11 20:46:59 Jinn dhclient: 
May 11 20:46:59 Jinn NetworkManager[870]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
May 11 20:46:59 Jinn dhclient: Listening on LPF/wlan0/00:e0:4c:d7:c0:59
May 11 20:46:59 Jinn dhclient: Sending on   LPF/wlan0/00:e0:4c:d7:c0:59
May 11 20:46:59 Jinn dhclient: Sending on   Socket/fallback
May 11 20:46:59 Jinn dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May 11 20:46:59 Jinn dhclient: DHCPOFFER of 192.168.2.4 from 192.168.2.1
May 11 20:46:59 Jinn dhclient: DHCPREQUEST of 192.168.2.4 on wlan0 to 255.255.255.255 port 67
May 11 20:47:16 Jinn dhclient: last message repeated 2 times
May 11 20:47:16 Jinn dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May 11 20:47:19 Jinn dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May 11 20:47:19 Jinn AptDaemon: INFO: Initializing daemon
May 11 20:47:26 Jinn dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May 11 20:47:43 Jinn dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May 11 20:47:44 Jinn NetworkManager[870]: <warn> (wlan0): DHCPv4 request timed out.
May 11 20:47:44 Jinn NetworkManager[870]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 3098
May 11 20:47:44 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
May 11 20:47:44 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
May 11 20:47:44 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
May 11 20:47:44 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
May 11 20:47:44 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
May 11 20:47:44 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
May 11 20:47:44 Jinn NetworkManager[870]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
May 11 20:47:44 Jinn NetworkManager[870]: <warn> Activation (wlan0) failed for access point (Narnia)
May 11 20:47:44 Jinn NetworkManager[870]: <info> Marking connection 'Auto Narnia' invalid.
May 11 20:47:44 Jinn NetworkManager[870]: <warn> Activation (wlan0) failed.
May 11 20:47:44 Jinn NetworkManager[870]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
May 11 20:47:44 Jinn NetworkManager[870]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
May 11 20:47:44 Jinn NetworkManager[870]: <info> (wlan0): deactivating device (reason: 0).
May 11 20:47:44 Jinn kernel: [ 4886.238049] wlan0: deauthenticating from 94:44:52:11:98:8b by local choice (reason=3)
```

---

### Post by marfal on 2011-05-13
I have a similar problem that started only this week with two installs of Natty, one desktop wired, and a laptop on wireless. Both will connect fine under windows. But neither will connect under natty.
Prior to last week everything was working fine. If I enter IP address and network details manually it will connect straight away, just won't work with DHCP on natty, all other non-natty devices connect with no issues.

So it appears to relate to the DHCP function on natty, has there been an update recently.

---

### Post by omega128 on 2011-05-13
Yes! disabling DHCP and using a static IP works!

Of course, it doesn't actually fix the problem; the DHCP still doesn't work right on wireless cards on Narwhal.  However, this *will* work for now.

Thank you!

---

### Post by ukberry on 2011-05-23
Same problem on a Dell Inspiron 1501 and a Packard Bell Easynote LJ71 :-(

Have temporarily allocated static IP addresses for home - having to use Windows when I'm at work :-(

---

### Post by HellesAngel on 2011-07-15
Did any of you try the live CD before installing?  I'm seeing very similar effects using an old Dell Latitude C540/C640 that connects to my WPA2 wireless network when booted from the 32 bit live CD, but using the same live CD to install on the hard disk produces an installation that never connects.  

Every time I select the WLAN the 'Wireless Network Authentication' dialog appears and then the connect fails, changing to static IP addresses has not helped.  This is now the second complete re-install, with and without installing the updates, and it just doesn't work.  Re-boot from the live CD and everything is fine.

Any ideas?

EDIT:
The most obvious problem is the ESSID it is trying to connect to is wrong/inconsistent:
> # **iwconfig eth1**
eth1      IEEE 802.11b  ESSID:"[COLOR=Red]EasyBox-BF3410[/COLOR]"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:08:BF:34:76   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=58/70  Signal level=-44 dBm  Noise level=-105 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:19
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
This is not the correct ESSID for my network, it is one of the neighbours', and not same name as appears in the NetworkMangler drop down connection list.  I have achieved a connection, but it was short lived, usually attempts to reconnect just cause NetworkMangler to create a new auto WLAN connection, and prompt for WLAN key again.  Something seems to be badly broken.

---

### Post by teddybairs1 on 2011-07-30
I have had the same problem after updating to Natty and using the ricotz-testing ppa.

---

