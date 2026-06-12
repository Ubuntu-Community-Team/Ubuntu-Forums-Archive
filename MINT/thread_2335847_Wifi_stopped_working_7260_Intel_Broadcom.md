---
title: "Wifi stopped working 7260 Intel Broadcom"
date: 2016-09-01
forum: MINT
---

### Post by piratskatt on 2016-09-01
I recently installed linux mint 18, everything was fine for 2 days but now the wifi doesn't work after a reboot.
I've tried downloading newer firmware files, disabling power management and finally upgrading my kernel, nothing seems to help. 

Computer is Lenovo thinkpad t440.

This is from ./wireless_info. Strangely the wifi-card seems to be working just fine from the iwlist scan  but somehow I can't connect.

Please help.

```


########## wireless info START ##########


Report from: 02 Sep 2016 02:30 CEST +0200


Booted last: 02 Sep 2016 00:00 CEST +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    LinuxMint
Description:    Linux Mint 18 Sarah
Release:    18
Codename:    sarah


##### kernel ############################


Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-LM [8086:155a] (rev 04)
    Subsystem: Lenovo ThinkPad X240 [17aa:2214]
    Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c270]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 04ca:7035 Lite-On Technology Corp. 
Bus 002 Device 004: ID 8087:07dc Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
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


enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF1]>  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d1a7:67e9:7298:1a30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91131 (91.1 KB)  TX bytes:100929 (100.9 KB)
          Interrupt:20 Memory:f0600000-f0620000 


wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


enp0s25   no wireless extensions.


wlp3s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp0s25
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s25
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s25


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2389     1  0 02:29 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection I218-LM (ThinkPad X240)
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.6-3
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
GENERAL.IP-IFACE:                       enp0s25
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       e38a7ed6-17a5-4f02-a318-b1a3c622e8aa
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e38a7ed6-17a5-4f02-a318-b1a3c622e8aa | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.7/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = Luddbollen
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.1.1
DHCP4.OPTION[11]:                       expiry = 1472862551
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.7
DHCP4.OPTION[17]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::d1a7:67e9:7298:1a30/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-AC 7260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-36-generic
GENERAL.FIRMWARE-VERSION:               17.352738.0
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Auto Tomater och Gurka]] (600 root)
[connection] id=Auto Tomater och Gurka | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=Tomater och Gurka
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Stockholm (based on set time zone)


country SE: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp0s25   no frequency information.


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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp0s25   Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)
      1   APs on   Frequency:5.2 GHz (Channel 40)
      1   APs on   Frequency:5.5 GHz (Channel 100)
      1   APs on   Frequency:5.68 GHz (Channel 136)


wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'ASUS N600' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"ASUS N600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000490b637d581
                    Extra: Last beacon: 2500ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Fyris' [AC2]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Fyris"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000103101465b49
                    Extra: Last beacon: 2472ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'comhem_EA29A6' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"comhem_EA29A6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000570c31a7a
                    Extra: Last beacon: 2444ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'jc' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"jc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001596ae0a3e1
                    Extra: Last beacon: 2384ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Tomater och Gurka' [AC5]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Tomater och Gurka"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000034098b45d1
                    Extra: Last beacon: 2356ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'B.R.' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"B.R."
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000043c23031c8
                    Extra: Last beacon: 2388ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Telia-2B8BB9' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Telia-2B8BB9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000030177996e3
                    Extra: Last beacon: 2200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'ComHem99FBB3' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"ComHem99FBB3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019d7dfb879c
                    Extra: Last beacon: 2288ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'comhem_555666' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"comhem_555666"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002ee0af4ac
                    Extra: Last beacon: 2180ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'anusbanan' [AC10]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"anusbanan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001983d8bc153
                    Extra: Last beacon: 2108ms ago
          Cell 11 - Address: <MAC 'Telia5GHz-2B8BB9' [AC11]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Telia5GHz-2B8BB9"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001953c1c9a2
                    Extra: Last beacon: 1992ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'comhem_EA29A6-5G' [AC12]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"comhem_EA29A6-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002ce4884803d
                    Extra: Last beacon: 1204ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'ComHem99FBB3-5G' [AC13]>
                    Channel:136
                    Frequency:5.68 GHz (Channel 136)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"ComHem99FBB3-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000021a834a643
                    Extra: Last beacon: 100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     49DC02934CB3D8C312FF8E1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


[mac80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


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


[    5.892603] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[    5.899667] iwlwifi 0000:03:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[    5.938813] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    5.939145] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    6.063283] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    6.198596] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    6.212196] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[    6.539185] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    6.539556] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[    6.755923] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    6.759619] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready (repeated 2 times)
[    8.130927] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   10.549697] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   10.549728] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
[   31.991745] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   32.189809] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated


########## wireless info END ############



```

---

### Post by jeremy31 on 2016-09-01
See if [code]sudo sed -i 's/managed=true/managed=false/' /etc/NetworkManager/NetworkManager.conf[code]

Reboot and see if it works

---

### Post by piratskatt on 2016-09-02
I changed that setting before to see if it would help. Someone on a thread said it could, but I'll change it back and reboot. 

ITS FIXED! 
The problem was apparently caused by me trying to connect to eduroam. The instructions provided said to configure wpa_supplicant.conf, reverting these changes has restored my wifi. 

I still need eduroam though.. Previously I've tried wicd but after reboot I couldn't get past login screen, is this a known error?

---

