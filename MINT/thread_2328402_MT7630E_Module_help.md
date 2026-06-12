---
title: "MT7630E Module help"
date: 2016-06-20
forum: MINT
---

### Post by rschanzenbacher on 2016-06-20
I know this topic is a bit overdone, but I want to know if a specific annoyance could be fixed. I add the module and install it using the included ".sh" files and it works until a kernel update. It does not recompile the module. Is there any way to recompile it? If you need info, tell me.


System Info:

Asus X555la Laptop
MediaTEK MT7630E

Driver used:

[https://github.com/neurobin/MT7630E/archive/release.zip](https://github.com/neurobin/MT7630E/archive/release.zip)

The install file has the following code:

```

#!/bin/bash
BASEDIR="$(dirname "$BASH_SOURCE")"
cd "$BASEDIR"
if (( $EUID != 0 )); then
    printf "\n-----Sorry! Run with root privilege\n\n"
    exit 1
fi
make
make install
modprobe mt7630e
modprobe mt76xx

```

The driver does include a 'dkms.conf' file so I do not know why dkms does not recompile this module.

---

### Post by jeremy31 on 2016-06-20
Can you post how you solved this issue as I am sure you won't be the only one to have this problem

---

### Post by rschanzenbacher on 2016-06-20
Well i read the README.md file and saw the answer was in the file but now I have the option to turn wireless on and off but networks do not show, this is where I am now.

---

### Post by jeremy31 on 2016-06-20
See the wireless script link in my signature then and post results

---

### Post by rschanzenbacher on 2016-06-20
```




########## wireless info START ##########


Report from: 20 Jun 2016 21:32 EDT -0400


Booted last: 20 Jun 2016 00:00 EDT -0400


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	LinuxMint
Description:	Linux Mint 18 Sarah
Release:	18
Codename:	sarah


##### kernel ############################


Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
	Subsystem: Foxconn International, Inc. MT7630e 802.11bgn Wireless Network Adapter [105b:e084]
	Kernel driver in use: mt7630e


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0489:e080 Foxconn / Hon Hai 
Bus 001 Device 003: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
mac80211              737280  1 mt7630e
sparse_keymap          16384  1 asus_wmi
cfg80211              565248  2 mac80211,mt7630e
wmi                    20480  1 asus_wmi
video                  40960  2 i915,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2bc1:ef8a:7406:4cab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9012 errors:0 dropped:47 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13470387 (13.4 MB)  TX bytes:1060623 (1.0 MB)


wlp3s0f0  Link encap:Ethernet  HWaddr <MAC 'wlp3s0f0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp3s0f0  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       775     1  0 18:27 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       68d84ecd-bd6e-41ad-8faa-2396ccffbd4d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   68d84ecd-bd6e-41ad-8faa-2396ccffbd4d | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.2/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.2
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1466476257
DHCP4.OPTION[22]:                       host_name = oem-X555LAB
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       ntp_servers = 192.168.1.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
DHCP4.OPTION[32]:                       requested_host_name = 1
DHCP4.OPTION[33]:                       next_server = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::2bc1:ef8a:7406:4cab/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp3s0f0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         MEDIATEK Corp.
GENERAL.PRODUCT:                        MT7630e 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         mt7630e
GENERAL.DRIVER-VERSION:                 4.4.0-24-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0f0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0f0
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
WIFI-PROPERTIES.5GHZ:                   no
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
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Auto Home]] (600 root)
[connection] id=Auto Home | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0f0' [IF2]> | mac-address-blacklist= | ssid=Home
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


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


enp2s0    no frequency information.


lo        no frequency information.


wlp3s0f0  14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz


##### iwlist scan #######################


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)


wlp3s0f0  Scan completed :
          Cell 01 - Address: <MAC 'optimumwifi' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=11 dBm  
                    Encryption key:off
                    ESSID:"optimumwifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000662963e4fd
                    Extra: Last beacon: 872ms ago
          Cell 02 - Address: <MAC 'Home' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=11 dBm  
                    Encryption key:on
                    ESSID:"Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000662965e562
                    Extra: Last beacon: 688ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[mac80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


[ 6342.905916] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 6342.923789] r8169 0000:02:00.0 enp2s0: link down
[ 6342.923874] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 6342.924868] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready
[ 6342.924916] ===>rt2x00lib_start
[ 6342.996430] rt2800pci_write_firmware: COM_REG0(0x730) = 0x1
[ 6342.996443] rt2800_load_firmware: COM_REG0(0x730) = 0x1
[ 6343.001875] ===>rt2x00lib_enable_radio
[ 6343.001919] ===>rt2800_enable_radio: 
[ 6343.002256] rt2800_init_bbp(): Init BBP Registers MT7630 (repeated 2 times)
[ 6343.003301] rt2800_init_bbp(): Init BBP Registers MT7630 complete
[ 6343.003302] ==>rt2800lib_init_queues
[ 6343.003320] <===rt2800lib_init_queues
[ 6343.003329] rt2800_enable_radio -7630 Dual antenna mode
[ 6343.017763] rt2800_init_rfcsr(): Init RF Registers MT7630
[ 6343.018159] rt2800_init_rfcsr: B0.R22 = 0x65
[ 6343.018176] rt2800_init_rfcsr(): Init RF Registers MT7630 complete
[ 6343.065917] rt2800pci_toggle_irq(1):Check if PDMA is idle!
[ 6343.065921] rt2800pci_toggle_irq(2):Check if PDMA is idle!
[ 6343.077883] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready (repeated 2 times)
[ 6345.461792] r8169 0000:02:00.0 enp2s0: link up
[ 6345.461810] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[ 6554.356763] wlp3s0f0: authenticate with <MAC 'Home' [AC2]>
[ 6554.362476] wlp3s0f0: send auth to <MAC 'Home' [AC2]> (try 1/3)
[ 6554.364380] wlp3s0f0: authenticated
[ 6554.366502] wlp3s0f0: associate with <MAC 'Home' [AC2]> (try 1/3)
[ 6554.371140] wlp3s0f0: RX AssocResp from <MAC 'Home' [AC2]> (capab=0x431 status=0 aid=9)
[ 6554.371157] ===>rt2800_sta_add:MT7630
[ 6554.371178] ===>rt2800_sta_add:MT7630   wcid=33
[ 6554.371611] ieee80211 phy0: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
[ 6554.381728] wlp3s0f0: associated
[ 6554.381743] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0f0: link becomes ready


########## wireless info END ############


```

Guess what? Fixed itself again! I kept rebooting and just gave the computer a break, came back and it worked! If you see anything in the log tell me though just in case. ;) Anyways thanks again!

---

### Post by howefield on 2016-06-21
Moved to the "*MINT*" sub forum.

---

