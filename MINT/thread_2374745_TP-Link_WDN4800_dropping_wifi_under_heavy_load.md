---
title: "TP-Link WDN4800 dropping wifi under heavy load"
date: 2017-10-18
forum: MINT
---

### Post by morefeo on 2017-10-18
Hi all,

I've got a TP Link WDN4800 (Atheros AR9380) which uses driver ath9k. Connected to a 5ghz band and under heavy loads (downloading Ubuntu image, for example) the speed gradually goes down until the wifi disconnects. This doesn't happen if I use the 2,4ghz band or in Windows 7. Additionally, this only happens when using the higher speed of the 5ghz band when for example downloading a big file, average internet browsing or gaming seems to not affect the stability.

Wifi script output:
```

########## wireless info START ##########

Report from: 18 Oct 2017 21:15 CEST +0200

Booted last: 18 Oct 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	LinuxMint
Description:	Linux Mint 18.2 Sonya
Release:	18.2
Codename:	sonya

##### kernel ############################

Linux 4.13.5-041305-generic #201710050600 SMP Thu Oct 5 10:02:44 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:859e]
	Kernel driver in use: r8169

04:00.0 Network controller [0280]: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:0030] (rev 01)
	Subsystem: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:3112]
	Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 062a:5918 Creative Labs 
Bus 003 Device 003: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 003 Device 002: ID 0d8c:0012 C-Media Electronics, Inc. 
Bus 003 Device 006: ID 1d19:1101 Dexatek Technology Ltd. DK DVB-T Dongle
Bus 003 Device 005: ID 046d:c31f Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl2832_sdr            36864  0
eeepc_wmi              16384  0
wmi_bmof               16384  0
videobuf2_vmalloc      16384  1 rtl2832_sdr
asus_wmi               28672  1 eeepc_wmi
mxm_wmi                16384  0
sparse_keymap          16384  1 asus_wmi
videobuf2_v4l2         24576  1 rtl2832_sdr
videobuf2_core         40960  2 rtl2832_sdr,videobuf2_v4l2
videodev              176128  3 videobuf2_core,rtl2832_sdr,videobuf2_v4l2
rtl2832                24576  1
i2c_mux                16384  1 rtl2832
dvb_usb_rtl28xxu       40960  1
dvb_usb_v2             40960  1 dvb_usb_rtl28xxu
dvb_core              126976  2 dvb_usb_v2,rtl2832
rc_core                36864  5 ir_lirc_codec,lirc_dev,dvb_usb_v2,dvb_usb_rtl28xxu
ath9k                 151552  0
ath9k_common           36864  1 ath9k
ath9k_hw              462848  2 ath9k,ath9k_common
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
mac80211              778240  1 ath9k
cfg80211              610304  4 mac80211,ath9k,ath,ath9k_common
wmi                    24576  3 asus_wmi,wmi_bmof,mxm_wmi
video                  40960  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21953 (21.9 KB)  TX bytes:21953 (21.9 KB)

wlp4s0    Link encap:Ethernet  HWaddr <MAC 'wlp4s0' [IF2]>  
          inet addr:192.168.0.157  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e8ad:d59a:33c0:a3a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1274142 (1.2 MB)  TX bytes:213034 (213.0 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

wlp4s0    IEEE 802.11  ESSID:"LebronFi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'LebronFi' [AN1]>   
          Bit Rate=104 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp4s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       861     1  0 21:13 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp4s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR93xx Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.13.5-041305-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp4s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.7/0000:04:00.0/net/wlp4s0
GENERAL.IP-IFACE:                       wlp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     LebronFi automática
GENERAL.CON-UUID:                       a1aea762-e652-41d1-8f01-073911852729
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     104 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a1aea762-e652-41d1-8f01-073911852729 | LebronFi automática
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   90007b3b-39c3-418c-b95a-e9acc2d3817b | LebronFi_5G automática
IP4.ADDRESS[1]:                         192.168.0.157/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1508440424
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.157
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       routers = 192.168.0.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::e8ad:d59a:33c0:a3a0/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/enp3s0
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

SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
LebronFi           <MAC 'LebronFi' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 
LebronFi_5G        <MAC 'LebronFi_5G' [AN2]>  Infra  36    5180 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
LebronFi           <MAC 'LebronFi' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2       yes     * 
HUAWEI-eA260-E6D2  <MAC 'HUAWEI-eA260-E6D2' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/LebronFi automática]] (600 root)
[connection] id=LebronFi automática | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp4s0' [IF2]> | mac-address-blacklist= | ssid=LebronFi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LebronFi]] (600 root)
[connection] id=LebronFi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=LebronFi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LebronFi_5G automática]] (600 root)
[connection] id=LebronFi_5G automática | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp4s0' [IF2]> | mac-address-blacklist= | ssid=LebronFi_5G
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LebronFi 1]] (600 root)
[connection] id=LebronFi 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=LebronFi
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Africa/Ceuta (based on set time zone)

country AW: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 20), (N/A)
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
	(5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS

##### iwlist channels ###################

lo        no frequency information.

enp3s0    no frequency information.

wlp4s0    32 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

wlp4s0    Failed to read scan data : Resource temporarily unavailable

enp3s0    Interface doesn't support scanning.

##### module infos ######################

[rtl2832_sdr]
filename:       /lib/modules/4.13.5-041305-generic/kernel/drivers/media/dvb-frontends/rtl2832_sdr.ko
license:        GPL
description:    Realtek RTL2832 SDR driver
author:         Antti Palosaari <crope@iki.fi>
srcversion:     37C01F74EBC9E76247733D3
depends:        videobuf2-v4l2,videodev,videobuf2-vmalloc,videobuf2-core
intree:         Y
name:           rtl2832_sdr
vermagic:       4.13.5-041305-generic SMP mod_unload 
parm:           emulated_formats:enable emulated formats (disappears in future) (bool)

[rtl2832]
filename:       /lib/modules/4.13.5-041305-generic/kernel/drivers/media/dvb-frontends/rtl2832.ko
license:        GPL
description:    Realtek RTL2832 DVB-T demodulator driver
author:         Antti Palosaari <crope@iki.fi>
author:         Thomas Mair <mair.thomas86@gmail.com>
srcversion:     5AE7E38690C81DBC0C6618D
depends:        dvb-core,i2c-mux
intree:         Y
name:           rtl2832
vermagic:       4.13.5-041305-generic SMP mod_unload 

[ath9k]
filename:       /lib/modules/4.13.5-041305-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     55EFCC9F539475103977285
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
name:           ath9k
vermagic:       4.13.5-041305-generic SMP mod_unload 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.13.5-041305-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8A1D2C60031409F8A50F895
depends:        ath9k_hw,cfg80211,ath
intree:         Y
name:           ath9k_common
vermagic:       4.13.5-041305-generic SMP mod_unload 

[ath9k_hw]
filename:       /lib/modules/4.13.5-041305-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF13127B5F7FC2736913C0C
depends:        ath
intree:         Y
name:           ath9k_hw
vermagic:       4.13.5-041305-generic SMP mod_unload 

[ath]
filename:       /lib/modules/4.13.5-041305-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
intree:         Y
name:           ath
vermagic:       4.13.5-041305-generic SMP mod_unload 

[mac80211]
filename:       /lib/modules/4.13.5-041305-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8F500F2EE3AF9C7436BAEE
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.5-041305-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.13.5-041305-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     26DEE587A73F75AF2ED02B8
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.5-041305-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl2832_sdr]
emulated_formats: N

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
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
bss_entries_limit: 1000
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

[/etc/pm/sleep.d/20-k290.sh] (755 root)
case "$1" in
    thaw|resume)
        /usr/local/sbin/k290_fnkeyctl > /dev/null
        ;;
    *) exit $NA
        ;;
esac
exit $?

##### udev rules ########################

##### dmesg #############################

[  145.624929] Modules linked in: ccm xpad ff_memless binfmt_misc snd_hda_codec_hdmi nvidia_uvm(POE) ir_lirc_codec lirc_dev rtl2832_sdr eeepc_wmi wmi_bmof videobuf2_vmalloc asus_wmi mxm_wmi videobuf2_memops sparse_keymap videobuf2_v4l2 videobuf2_core videodev media fc0013 intel_rapl rtl2832 x86_pkg_temp_thermal i2c_mux intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc joydev aesni_intel aes_x86_64 crypto_simd glue_helper cryptd arc4 input_leds intel_cstate dvb_usb_rtl28xxu dvb_usb_v2 dvb_core rc_core nvidia_drm(POE) nvidia_modeset(POE) snd_usb_audio snd_usbmidi_lib nvidia(POE) snd_hda_codec_realtek snd_hda_codec_generic intel_rapl_perf snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep ath9k ath9k_common snd_pcm ath9k_hw snd_seq_midi ath snd_seq_midi_event
[  145.625218]  ? ath9k_cmn_rx_skb_postprocess+0x4b/0x130 [ath9k_common]
[  145.625235]  ath_rx_tasklet+0xa75/0xf70 [ath9k]
[  145.625252]  ath9k_tasklet+0x169/0x240 [ath9k]
[  146.034352] Modules linked in: ccm xpad ff_memless binfmt_misc snd_hda_codec_hdmi nvidia_uvm(POE) ir_lirc_codec lirc_dev rtl2832_sdr eeepc_wmi wmi_bmof videobuf2_vmalloc asus_wmi mxm_wmi videobuf2_memops sparse_keymap videobuf2_v4l2 videobuf2_core videodev media fc0013 intel_rapl rtl2832 x86_pkg_temp_thermal i2c_mux intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc joydev aesni_intel aes_x86_64 crypto_simd glue_helper cryptd arc4 input_leds intel_cstate dvb_usb_rtl28xxu dvb_usb_v2 dvb_core rc_core nvidia_drm(POE) nvidia_modeset(POE) snd_usb_audio snd_usbmidi_lib nvidia(POE) snd_hda_codec_realtek snd_hda_codec_generic intel_rapl_perf snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep ath9k ath9k_common snd_pcm ath9k_hw snd_seq_midi ath snd_seq_midi_event
[  146.034433]  ? ath9k_cmn_rx_skb_postprocess+0x4b/0x130 [ath9k_common]
[  146.034438]  ath_rx_tasklet+0xa75/0xf70 [ath9k]
[  146.034441]  ath9k_tasklet+0x169/0x240 [ath9k]

########## wireless info END ############

```

---

### Post by morefeo on 2017-10-20
Hmm no one?

---

### Post by praseodym on 2017-10-20
Try disabling the hardware encryption:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by morefeo on 2017-10-20
Hello, thank you for replying.

I tried that already. It helps a little; instead of disconnecting the speed is cut in half, then recovers, then it's cut again, and repeat.

Any more options to disable that might help?

---

### Post by jeremy31 on 2017-10-20
I would file a bug report, see [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) to start, file the bug against package Linux as there seems to be issues with wifi signal strength variations using 5 Ghz

---

### Post by praseodym on 2017-10-21
The Network "LebronFi" is available 2 times, plus the 5 GHz one. Please show the output os

```
sudo iwlist scan
```

---

### Post by morefeo on 2017-10-21
Here's the output:
```
wlp4s0    Scan completed :
          Cell 01 - Address: 78:81:02:21:62:F1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000043fb2fa4b1
                    Extra: Last beacon: 2788ms ago
                    IE: Unknown: 00080000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B0501001C0000
                    IE: Unknown: 2D1ABC091BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: DD090010180201000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 84:BE:52:B9:E6:D3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"HUAWEI-eA260-E6D2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000404ff602ab
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00114855415745492D65413236302D45364432
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABC191AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD090010180204000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
          Cell 03 - Address: 78:81:02:21:62:F2
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"LebronFi_5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000043fb1d28bb
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 000B4C6562726F6E46695F3547
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 07344445202401172801172C01173001173401173801173C011740011764011E68011E6C011E70011E74011E84011E88011E8C011E00
                    IE: Unknown: 200100
                    IE: Unknown: 23021100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050300040000
                    IE: Unknown: 2D1AEF091BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050400000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: BF0CB259820FEAFF0000EAFF0000
                    IE: Unknown: C005012A000000
                    IE: Unknown: C30402020202
                    IE: Unknown: DD090010180203001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

---

### Post by jeremy31 on 2017-10-21
*Thread moved to **MINT**.*
Why are you using a 4.13 kernel?  Do you have the same issue in a kernel provided by the Update Manager?

---

### Post by morefeo on 2017-10-21
Yes, I updated the kernel in case something was fixed recently.

---

### Post by praseodym on 2017-10-22
Your 2,4 GHz network is hidden? This is NOT a security feature. For this one

```
Cell 03 - Address: [COLOR="#FF0000"]78:81:02:21:62:F2
[/COLOR]                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"LebronFi_5G"
```
add its MAC address into the field BSSID in your network profile and reconnect

---

### Post by morefeo on 2017-10-26
That... actually worked. Big thanks.

May I ask why?

---

