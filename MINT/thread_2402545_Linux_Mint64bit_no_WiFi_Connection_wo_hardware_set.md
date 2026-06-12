---
title: "Linux Mint64bit no WiFi Connection w/o hardware settings to enable it."
date: 2018-10-01
forum: MINT
---

### Post by kindman103 on 2018-10-01
Hello - I think and know that there are a lot of other thread that handle told the same problem. I want to enable WiFi on my old notebook. Have installed LinuxMint 64 bit on it. All works great except the WiFi. There is no switch or function key to enable it (FN + F7 doesn't work) 

I have done some research to get information from my PC. Sorry I am new at Linux and I think I need some help with the syntax I have to follow to fix that Problem. 


```

########## wireless info START ##########

Report from: 01 Oct 2018 16:27 CEST +0200

Booted last: 01 Oct 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 19 Tara
Release:    19
Codename:    tara

##### kernel ############################

Linux 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

MATE

##### lspci #############################

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Wistron Corp. RTL8101e Medion WIM 2210 Notebook PC [MD96850] [17c0:1053]
    Kernel driver in use: r8169

0a:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation WM3945ABG MOW2 [8086:1001]
    Kernel driver in use: iwl3945

##### lsusb #############################

Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0102 Acer, Inc Crystal Eye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 062a:5918 Creative Labs 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

iwl3945                73728  0
iwlegacy               98304  1 iwl3945
mac80211              778240  2 iwlegacy,iwl3945
cfg80211              622592  3 mac80211,iwlegacy,iwl3945
wmi_bmof               16384  0
wmi                    24576  1 wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.174.180  netmask 255.255.255.0  broadcast 192.168.174.255
        inet6 2a02:8108:97c0:3b54:5145:c989:1e3b:7f74  prefixlen 64  scopeid 0x0<global>
        inet6 2a02:8108:97c0:3b54:5011:f8ba:25b2:bb80  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::e4da:5056:40d1:15d2  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 15808  bytes 17888003 (17.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 9200  bytes 936192 (936.1 KB)
        TX errors 14  dropped 0 overruns 0  carrier 14  collisions 735

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 7305  bytes 491033 (491.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7305  bytes 491033 (491.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp10s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp6s0    no wireless extensions.

lo        no wireless extensions.

wlp10s0   IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.174.1   0.0.0.0         UG    100    0        0 enp6s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp6s0
192.168.174.0   0.0.0.0         255.255.255.0   U     100    0        0 enp6s0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       827     1  0 13:19 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp6s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller (RTL8101e Medion WIM 2210 Notebook PC [MD96850])
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/net/enp6s0
GENERAL.IP-IFACE:                       enp6s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       beb278d5-8f2c-3c0e-96f7-7f86280c99be
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.174.180/24
IP4.GATEWAY:                            192.168.174.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.174.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.174.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.174.1
DHCP4.OPTION[1]:                        requested_domain_search = 1
DHCP4.OPTION[2]:                        requested_broadcast_address = 1
DHCP4.OPTION[3]:                        requested_domain_name = 1
DHCP4.OPTION[4]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        dhcp_server_identifier = 192.168.174.110
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1538497138
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       routers = 192.168.174.1
DHCP4.OPTION[15]:                       ip_address = 192.168.174.180
DHCP4.OPTION[16]:                       requested_domain_name_servers = 1
DHCP4.OPTION[17]:                       domain_name_servers = 192.168.174.1
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       broadcast_address = 192.168.174.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.174.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       requested_static_routes = 1
IP6.ADDRESS[1]:                         2a02:8108:97c0:3b54:5145:c989:1e3b:7f74/64
IP6.ADDRESS[2]:                         2a02:8108:97c0:3b54:5011:f8ba:25b2:bb80/64
IP6.ADDRESS[3]:                         fe80::e4da:5056:40d1:15d2/64
IP6.GATEWAY:                            fe80::464e:6dff:fe00:ad6e
IP6.ROUTE[1]:                           dst = 2a02:8108:97c0:3b54::/62, nh = fe80::464e:6dff:fe00:ad6e, mt = 100
IP6.ROUTE[2]:                           dst = 2a02:8108:97c0:3b54::/64, nh = ::, mt = 100
IP6.ROUTE[3]:                           dst = ::/0, nh = fe80::464e:6dff:fe00:ad6e, mt = 100
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[6]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.DNS[1]:                             fd00::464e:6dff:fe00:ad6e
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd00::464e:6dff:fe00:ad6e
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:44:4e:6d:0:ad:6e
DHCP6.OPTION[4]:                        dhcp6_unknown_86 = 2a:2:81:8:97:c0:3b:54:46:4e:6d:ff:fe:0:ad:6e
DHCP6.OPTION[5]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[6]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:ba:1d:8d:a6:35:c8:f0:c0:35:df:db:99:1f:aa:98:4c
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   beb278d5-8f2c-3c0e-96f7-7f86280c99be | Wired connection 1

GENERAL.DEVICE:                         wlp10s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        PRO/Wireless 3945ABG [Golan] Network Connection (WM3945ABG MOW2)
GENERAL.DRIVER:                         iwl3945
GENERAL.DRIVER-VERSION:                 4.15.0-34-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:0a:00.0/net/wlp10s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WLAN-8X37D4
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/1-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp6s0    no frequency information.

lo        no frequency information.

wlp10s0   32 channels in total; available frequencies :
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
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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

##### iwlist scan #######################

enp6s0    Interface doesn't support scanning.

wlp10s0   Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[iwl3945]
filename:       /lib/modules/4.15.0-34-generic/kernel/drivers/net/wireless/intel/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     EA6C390E3EE9D882117A562
depends:        iwlegacy,mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           iwl3945
vermagic:       4.15.0-34-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/4.15.0-34-generic/kernel/drivers/net/wireless/intel/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     9063671900A959E01DEF3FB
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           iwlegacy
vermagic:       4.15.0-34-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/4.15.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     76870094CC01F4AC06240B7
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-34-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-34-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1

[iwlegacy]
bt_coex_active: Y
led_mode: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############


```

---

### Post by wildmanne39 on 2018-10-01
*Thread moved to **MINT for a more appropriate fit**.*

---

### Post by praseodym on 2018-10-01
Any button, switch, key or key combo to turn wifi on? Tried to reset the BIOS to default settings?

---

### Post by kindman103 on 2018-10-02
There is no switch or function key to enable it (FN + F7 doesn't work) no hardware button to use for activate the power mode of the WiFi. 
Default settings in BIOS do not result in a difference of the function - it is a MEDION MD96350 
the SUDO rfkill list result with "Hard blocked: yes "

---

