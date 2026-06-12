---
title: "Wifi Problem  Atheros AR9462  on Acer Aspire 5-531"
date: 2016-12-18
forum: MINT
---

### Post by Dirk_Ouellette on 2016-12-18
As recommended in [https://ubuntuforums.org/showthread.php?p=12350385#post12350385](https://ubuntuforums.org/showthread.php?p=12350385#post12350385)


```
########## wireless info START

Report from: 18 Dec 2016 09:49 PST -0800

Booted last: 18 Dec 2016 00:00 PST -0800

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 18 Sarah
Release:    18
Codename:    sarah

##### kernel ############################

Linux 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:58:04 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

02:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:0724]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Lite-On Communications Inc AR9462 Wireless Network Adapter [11ad:6621]
    Kernel driver in use: ath9k

##### lsusb 

Bus 002 Device 003: ID 064e:d251 Suyin Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04ca:3006 Lite-On Technology Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 004: ID 04f9:024a Brother Industries, Ltd 
Bus 003 Device 003: ID 4971:ce07 SimpleTech 
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 135168  0
ath9k_common           36864  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    24576  3 ath9k_common,ath9k,ath9k_hw
mac80211              659456  1 ath9k
cfg80211              499712  4 ath,ath9k_common,ath9k,mac80211
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
ath3k                  16384  0
bluetooth             479232  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
wmi                    20480  1 acer_wmi
video                  36864  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0f2  Link encap:Ethernet  HWaddr <MAC 'enp2s0f2' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1cb6:4c52:49c3:e463/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61319221 (61.3 MB)  TX bytes:5057464 (5.0 MB)

##### iwconfig ##########################

enp2s0f2  no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abgn  ESSID:"lightspeed2.4"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'lightspeed2.4' [AC1]>   
          Bit Rate=240 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:143   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       901     1  0 08:13 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9462 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-53-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto lightspeed2.4
GENERAL.CON-UUID:                       dfb5736a-91f2-4645-a158-7a275ef7379f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     240 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   dfb5736a-91f2-4645-a158-7a275ef7379f | Auto lightspeed2.4
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   f8155968-1f0e-4cd7-bafd-612d195c82a1 | Auto dlink-30FA
IP4.ADDRESS[1]:                         192.168.1.10/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1482169498
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.10
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::1cb6:4c52:49c3:e463/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0f2' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.2/net/enp2s0f2
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

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
lightspeed5    <MAC 'lightspeed5' [AC3]>  Infra  161   5805 MHz  54 Mbit/s  64   WPA1 WPA2  no        
lightspeed2.4  <MAC 'lightspeed2.4' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  63   WPA1 WPA2  yes     * 
dlink-30FA     <MAC 'dlink-30FA' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  60   WPA1 WPA2  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Auto lightspeed2.4]] (600 root)
[connection] id=Auto lightspeed2.4 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=lightspeed2.4
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto dlink-30FA]] (600 root)
[connection] id=Auto dlink-30FA | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=dlink-30FA
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Vancouver (based on set time zone)

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

enp2s0f2  no frequency information.

lo        no frequency information.

wlp3s0    32 channels in total; available frequencies :
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
          Current Frequency=2.437 GHz (Channel 6)

##### iwlist scan #######################

enp2s0f2  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:5.805 GHz

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'lightspeed2.4' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"lightspeed2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000026949c2a7e
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'dlink-30FA' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"dlink-30FA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019b30b7ebf0
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'lightspeed5' [AC3]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"lightspeed5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026937b705f
                    Extra: Last beacon: 392ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.4.0-53-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     1B84AD8C53440158CD581F2
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 686 
parm:           debugging mask (uint)
parm:           nohwcrypt: disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.4.0-53-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 686 

[ath9k_hw]
filename:       /lib/modules/4.4.0-53-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     FA7ECFBA5761A5B3ED96BB2
depends:        ath
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 686 

[ath]
filename:       /lib/modules/4.4.0-53-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-53-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-53-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ath3k]
filename:       /lib/modules/4.4.0-53-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     2B85DCB887D9376A61652DD
depends:        bluetooth
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 686 

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 1
ps_enable: 0
use_chanctx: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 5028.892811] wlp3s0: deauthenticating from <MAC 'lightspeed2.4' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5037.286281] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[ 5040.778974] wlp3s0: authenticate with <MAC 'lightspeed2.4' [AC1]>
[ 5040.794640] wlp3s0: send auth to <MAC 'lightspeed2.4' [AC1]> (try 1/3)
[ 5040.797222] wlp3s0: authenticated
[ 5040.801192] wlp3s0: associate with <MAC 'lightspeed2.4' [AC1]> (try 1/3)
[ 5040.804859] wlp3s0: RX AssocResp from <MAC 'lightspeed2.4' [AC1]> (capab=0x431 status=0 aid=3)
[ 5040.804999] wlp3s0: associated
[ 5040.805080] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 5063.222973] wlp3s0: deauthenticating from <MAC 'lightspeed2.4' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5066.586436] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[ 5070.197036] wlp3s0: authenticate with <MAC 'lightspeed2.4' [AC1]>
[ 5070.208352] wlp3s0: send auth to <MAC 'lightspeed2.4' [AC1]> (try 1/3)
[ 5070.210356] wlp3s0: authenticated
[ 5070.213675] wlp3s0: associate with <MAC 'lightspeed2.4' [AC1]> (try 1/3)
[ 5070.217300] wlp3s0: RX AssocResp from <MAC 'lightspeed2.4' [AC1]> (capab=0x431 status=0 aid=3)
[ 5070.217421] wlp3s0: associated
[ 5070.217481] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 5451.031350] wlp3s0: deauthenticating from <MAC 'lightspeed2.4' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5462.323647] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[ 5465.937193] wlp3s0: authenticate with <MAC 'lightspeed2.4' [AC1]>
[ 5465.955392] wlp3s0: send auth to <MAC 'lightspeed2.4' [AC1]> (try 1/3)
[ 5465.957387] wlp3s0: authenticated
[ 5465.959468] wlp3s0: associate with <MAC 'lightspeed2.4' [AC1]> (try 1/3)
[ 5465.963085] wlp3s0: RX AssocResp from <MAC 'lightspeed2.4' [AC1]> (capab=0x431 status=0 aid=3)
[ 5465.963207] wlp3s0: associated
[ 5465.963265] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 5469.339244] wlp3s0: deauthenticating from <MAC 'lightspeed2.4' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5472.857119] wlp3s0: authenticate with <MAC 'lightspeed2.4' [AC1]>
[ 5472.877140] wlp3s0: send auth to <MAC 'lightspeed2.4' [AC1]> (try 1/3)
[ 5472.879306] wlp3s0: authenticated
[ 5472.887568] wlp3s0: associate with <MAC 'lightspeed2.4' [AC1]> (try 1/3)
[ 5472.891472] wlp3s0: RX AssocResp from <MAC 'lightspeed2.4' [AC1]> (capab=0x431 status=0 aid=3)
[ 5472.891640] wlp3s0: associated

########## wireless info END ############
```

---

### Post by jeremy31 on 2016-12-18
*Thread moved to **MINT**.*
Please use code tags on script results and terminal output

---

### Post by Dirk_Ouellette on 2016-12-18
I do not understand how to use code tags. I am wondering if the Atheros AR9462 has gone south on me.

---

### Post by jeremy31 on 2016-12-18
See the code tags link in my signature, it basically involves using [noparse]```
 before the output and 
``` after the output[/noparse]
In the advanced reply you will see a # that will place code tags and you can just paste the info

It appears that the encryption used by the lightspeed access point may be causing the issue as it is using TKIP encryption, WPA2-AES or WPA2-PSK is usually preferred in Linux

If you have a post at forums.linuxmint.com(or elsewhere) please post a link so I can see what others may have suggested or what you have attempted

---

### Post by Dirk_Ouellette on 2016-12-18
Thank you! I will study a bit and try my hand at it...

---

### Post by Dirk_Ouellette on 2016-12-19
My router has TKIP+AES under WPA/WPI encryption and I can't change it to AES alone. The router has WPA2/WPA-WPA  under Network Authentication.

---

### Post by Dirk_Ouellette on 2016-12-19
I followed this fix to no avail.  [https://digitz.org/blog/wifi-issue-on-acer-laptops-running-linux-qualcomm-atheros-device-0042/](https://digitz.org/blog/wifi-issue-on-acer-laptops-running-linux-qualcomm-atheros-device-0042/)

Today's update of network modules did nought to repair the issue.

I am preparing to buy a linux compatible USB network adapter, and see if that doesn't solve this.

---

### Post by jeremy31 on 2016-12-20
See if WPA/WPA2 works better and uninstall the fix you tried ```
cd backports-20151120
sudo make uninstall
```

Reboot

Somehow I believe that the fix you found was plagiarized from posts made over a year ago and isn't needed even for the device mentioned anymore in LM18

---

### Post by Dirk_Ouellette on 2016-12-20
Thank you Jeremy. Today, suddenly, wifi is working! ?????  The machine gremlins must have been busy? Mercury is retrograde?  I held my nose right?  My sweet departed Mom has been active on my behalf? The world ends tomorrow?

---

