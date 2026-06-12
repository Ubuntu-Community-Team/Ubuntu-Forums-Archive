---
title: "I upgraded to ubuntu 16.04 but now this!!!"
date: 2016-08-05
forum: Installation &amp; Upgrades
---

### Post by ezra9697 on 2016-08-05
I have been using ubuntu for a while but I  still believe I'm a newbie. So here's messed up brief on why my linux upgrade ddidnt go well. I upgraded the Os without forgetting to connect my laptop charger and I left it to to other stuff. Comin back I booted it to revovery mode and had what looked like an undone installation done. But the problem that bothers me is not being able to connect to the internet via wlan0. So searching somethreads i came across the wireless script and ran it but  i'm finding it hard to understand whats goin on. Any help or advise is very much appreciated! 

Here is the info:

```

########## wireless info START ##########

Report from: 04 Aug 2016 17:21 SAST +0200

Booted last: 04 Aug 2016 00:00 SAST +0200

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3821]
	Kernel driver in use: r8169

03:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
	Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:07dc Intel Corp. 
Bus 001 Device 003: ID 13d3:5727 IMC Networks 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
ideapad_laptop         24576  0
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.0.1
nameserver 199.175.54.136
nameserver 23.94.123.134

##### network managers ##################

Installed:

	NetworkManager

Running:

root      2621     1  0 16:26 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               16.242414.0
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{17,28}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   cff8b357-86b5-4744-b168-56f8be1e5f75 | kamva9697
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   9c809fc6-b7ec-48bf-be8b-6e285693929a | INet_1

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         ttyACM0
GENERAL.TYPE:                           modem
GENERAL.NM-TYPE:                        NMDeviceModem
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         cdc_acm
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            0
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /org/freedesktop/ModemManager1/Modem/1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                      BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
"CShare_MediaPad_huawei"  <MAC '"CShare_MediaPad_huawei"' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  20      â–‚___  --        no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC 'eth0' [IF1]>,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/MTN World-class Internet 1902]] (600 root)
[connection] id=MTN World-class Internet 1902 | type=802-11-wireless
[802-11-wireless] ssid=MTN World-class Internet 1902 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidHotspot6143]] (600 root)
[connection] id=AndroidHotspot6143 | type=802-11-wireless
[802-11-wireless] ssid=AndroidHotspot6143 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Central University of Technology]] (600 root)
[connection] id=Central University of Technology | type=802-11-wireless
[802-11-wireless] ssid=Central University of Technology | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/CUT-Guest]] (600 root)
[connection] id=CUT-Guest | type=802-11-wireless
[802-11-wireless] ssid=CUT-Guest | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Serram-Wkm]] (600 root)
[connection] id=Serram-Wkm | type=802-11-wireless
[802-11-wireless] ssid=Serram-Wkm | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Chari-spot]] (600 root)
[connection] id=Chari-spot | type=802-11-wireless
[802-11-wireless] ssid=Chari-spot | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidHotspot7438]] (600 root)
[connection] id=AndroidHotspot7438 | type=802-11-wireless
[802-11-wireless] ssid=AndroidHotspot7438 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Lephola]] (600 root)
[connection] id=Lephola | type=802-11-wireless
[802-11-wireless] ssid=Lephola | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/kamva9697]] (600 root)
[connection] id=kamva9697 | type=802-11-wireless
[802-11-wireless] ssid=kamva9697 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BsVU-cGF1bA]] (600 root)
[connection] id=BsVU-cGF1bA | type=802-11-wireless
[802-11-wireless] ssid=BsVU-cGF1bA | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Leech97]] (600 root)
[connection] id=Leech97 | type=802-11-wireless
[802-11-wireless] ssid=Leech97 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Inconet-Silo]] (600 root)
[connection] id=Inconet-Silo | type=802-11-wireless
[802-11-wireless] ssid=Inconet-Silo | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Bnl4-dGhhYmlzYQ]] (600 root)
[connection] id=Bnl4-dGhhYmlzYQ | type=802-11-wireless
[802-11-wireless] ssid=Bnl4-dGhhYmlzYQ | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Eduroam]] (600 root)
[connection] id=Eduroam | type=802-11-wireless
[802-11-wireless] ssid=Eduroam | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/BYUS-dGhhYmlzZWxvYW5l]] (600 root)
[connection] id=BYUS-dGhhYmlzZWxvYW5l | type=802-11-wireless
[802-11-wireless] ssid=BYUS-dGhhYmlzZWxvYW5l | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/UFS_Wireless1]] (600 root)
[ipv6] method=auto
[connection] id=UFS_Wireless1 | type=802-11-wireless
[802-11-wireless] ssid=UFS_Wireless1 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/CUT-Staff]] (600 root)
[ipv6] method=auto
[connection] id=CUT-Staff | type=802-11-wireless
[802-11-wireless] ssid=CUT-Staff | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/INet_1]] (600 root)
[connection] id=INet_1 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=INet_1 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Xperia E4g_df40]] (600 root)
[connection] id=Xperia E4g_df40 | type=802-11-wireless
[802-11-wireless] ssid=Xperia E4g_df40 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MWEB_34A0C5]] (600 root)
[connection] id=MWEB_34A0C5 | type=802-11-wireless
[802-11-wireless] ssid=MWEB_34A0C5 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/D-Link]] (600 root)
[connection] id=D-Link | type=802-11-wireless
[802-11-wireless] ssid=D-Link | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/kamva9697 1]] (600 root)
[connection] id=kamva9697 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=kamva9697
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BI2k-bW90YWJlc3MubGVib2dhbmc]] (600 root)
[connection] id=BI2k-bW90YWJlc3MubGVib2dhbmc | type=802-11-wireless
[802-11-wireless] ssid=BI2k-bW90YWJlc3MubGVib2dhbmc | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/CUT-Students]] (600 root)
[ipv6] method=auto
[connection] id=CUT-Students | type=802-11-wireless
[802-11-wireless] ssid=CUT-Students | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto

##### iw reg get ########################

Region: Africa/Johannesburg (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC '"CShare_MediaPad_huawei"' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:""CShare_MediaPad_huawei""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000065dacc3fa
                    Extra: Last beacon: 3224ms ago

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     49DC02934CB3D8C312FF8E1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b4 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 2214.249991] r8169 0000:02:00.0 eth0: link down
[ 2215.141737] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.0.1.2d.d.bseq
[ 2215.265735] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 2216.849356] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2216.862995] r8169 0000:02:00.0 eth0: link down
[ 2216.863065] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2216.864747] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2216.865897] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[ 2216.997230] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############
```

---

