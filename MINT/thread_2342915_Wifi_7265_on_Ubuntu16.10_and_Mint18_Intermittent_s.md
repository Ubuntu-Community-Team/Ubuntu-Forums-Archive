---
title: "Wifi 7265 on Ubuntu16.10 and Mint18: Intermittent slow Internet with good connection"
date: 2016-11-11
forum: MINT
---

### Post by TuxManRemove on 2016-11-11
Hello
Now "wavemon" gives a 73% connection quality, adn I dont will be able to send this post.

I have tested it with several router, at work, in the library, coffe, home, and it always happens the same. If I'm not next to the router, I move 10 meters or 12, browsing is hopeless.
I  try to open a web and sometimes load and sometimes do not load,  sometimes the wenn browser displays the timeout message and F5 pulse and  loads the web. 
Load 1 of every 4 pages I try to open.
The speednet.net speed checks sometimes work at 15Mbs and sometimes tells me that it can not connect and can not do the test.

I have tried Ubuntu 16 and Linux Mint 18

I do not know what to do.

Thank you very much.

```

  ########## wireless info START ##########

Report from: 11 Nov 2016 12:46 CET +0100

Booted last: 11 Nov 2016 00:00 CET +0100

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	LinuxMint
Description:	Linux Mint 18 Sarah
Release:	18
Codename:	sarah

##### kernel ############################

Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

MATE

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:0123]
	Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 2b)
	Subsystem: Intel Corporation Dual Band Wireless-N 7265 [8086:5000]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 090c:037c Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 300k Pixel Camera
Bus 001 Device 003: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::165e:da87:5195:3428/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3555353 (3.5 MB)  TX bytes:422031 (422.0 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"WLAN22_Guest"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'WLAN22_Guest' [AC1]>   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:203   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.2.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
nameserver 8.8.8.8
nameserver 8.8.4.4

##### network managers ##################

Installed:

	NetworkManager

Running:

root       819     1  0 12:42 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-N 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               17.311016.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WLAN22_Guest
GENERAL.CON-UUID:                       1139e4f7-83bf-4671-b61e-0732aa9420ee
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     270 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1139e4f7-83bf-4671-b61e-0732aa9420ee | WLAN22_Guest
IP4.ADDRESS[1]:                         192.168.2.105/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
IP4.DNS[3]:                             192.168.2.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1478871744
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.2.105
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.2.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 8.8.8.8 8.8.4.4 192.168.2.1 0.0.0.0
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.2.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.2.1
IP6.ADDRESS[1]:                         fe80::165e:da87:5195:3428/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
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

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
WLAN22_Guest     <MAC 'WLAN22_Guest' [AC1]>  Infra  7     2442 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2    yes     * 
_AUTO_ONOWiFi    <MAC '_AUTO_ONOWiFi' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2 802.1X  no        
ONO416C          <MAC 'ONO416C' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2    no        
_ONOWiFi         <MAC '_ONOWiFi' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  --           no        
_AUTO_ONOWiFi    <MAC '_AUTO_ONOWiFi' [AN5]>  Infra  13    2472 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2 802.1X  no        
ONO0DB5          <MAC 'ONO0DB5' [AC10]>  Infra  13    2472 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2    no        
NETGEAR_GUEST_2  <MAC 'NETGEAR_GUEST_2' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
_ONOWiFi         <MAC '_ONOWiFi' [AC7]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  --           no        
_AUTO_ONOWiFi    <MAC '_AUTO_ONOWiFi' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2 802.1X  no        
_ONOWiFi         <MAC '_ONOWiFi' [AN10]>  Infra  13    2472 MHz  54 Mbit/s  40      &#9602;&#9604;__  --           no        
JRC              <MAC 'JRC' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2         no        
--               <MAC '##########' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2    no        
WLAN22_5G        <MAC 'WLAN22_5G' [AC11]>  Infra  36    5180 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2         no        

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

[[/etc/NetworkManager/system-connections/WLAN22_Guest]] (600 root)
[connection] id=WLAN22_Guest | type=wifi | permissions=user:laptop:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=WLAN22_Guest
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country IS: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 20), (N/A)
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
	(5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      6   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)
      1   APs on   Frequency:5.18 GHz (Channel 36)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'WLAN22_Guest' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"WLAN22_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000015668cb66
                    Extra: Last beacon: 380ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'JRC' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"JRC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ba327ef8ce
                    Extra: Last beacon: 588ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ONO416C' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"ONO416C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000285485776
                    Extra: Last beacon: 588ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '_AUTO_ONOWiFi' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"_AUTO_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002854860b9
                    Extra: Last beacon: 584ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC '_ONOWiFi' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000285486921
                    Extra: Last beacon: 584ms ago
          Cell 06 - Address: <MAC '_AUTO_ONOWiFi' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"_AUTO_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ba327f1e70
                    Extra: Last beacon: 580ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC '_ONOWiFi' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"_ONOWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ba327f271f
                    Extra: Last beacon: 580ms ago
          Cell 08 - Address: <MAC 'vodafone1045' [AC8]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"vodafone1045"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000083f18a381c
                    Extra: Last beacon: 520ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '##########' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000288f1b17c
                    Extra: Last beacon: 156ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'ONO0DB5' [AC10]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ONO0DB5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000036e5756ee
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'WLAN22_5G' [AC11]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"WLAN22_5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000015b10a612
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     49DC02934CB3D8C312FF8E1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
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
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 5
power_save: N
swcrypto: 0
uapsd_disable: Y

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

blacklist ath9k

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
options iwlwifi 11n_disable=8 power_save=0 power_level=5
options iwlwifi bt_coex_active=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

rfkill block bluetooth
exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    5.027553] iwlwifi 0000:02:00.0: Unsupported splx structure
[    5.043017] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265-19.ucode failed with error -2
[    5.043146] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265-18.ucode failed with error -2
[    5.052098] iwlwifi 0000:02:00.0: loaded firmware version 17.311016.0 op_mode iwlmvm
[    5.092705] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless N 7265, REV=0x184
[    5.092984] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    5.163436] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    5.270647] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    6.128087] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    6.329499] r8169 0000:01:00.0 enp1s0: link down
[    6.329538] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    6.334893] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    6.335010] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[    6.408672] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[   13.738294] wlp2s0: authenticate with <MAC 'WLAN22_Guest' [AC1]>
[   13.740813] wlp2s0: send auth to <MAC 'WLAN22_Guest' [AC1]> (try 1/3)
[   13.742553] wlp2s0: authenticated
[   13.742722] wlp2s0: associate with <MAC 'WLAN22_Guest' [AC1]> (try 1/3)
[   13.747756] wlp2s0: RX AssocResp from <MAC 'WLAN22_Guest' [AC1]> (capab=0x411 status=0 aid=2)
[   13.755561] wlp2s0: associated
[   13.755634] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

########## wireless info END ############


```

---

### Post by howefield on 2016-11-11
Thread moved to the "*MINT*" sub forum.

---

### Post by jeremy31 on 2016-11-11
It seems that power management is enabled for the wifi
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Then restart network manager with
```
systemctl restart network-manager.service
```

---

### Post by TuxManRemove on 2016-11-11
Hello,
I do it, and reboot.
The problem continue.

---

