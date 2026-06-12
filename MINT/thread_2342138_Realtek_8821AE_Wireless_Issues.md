---
title: "Realtek 8821AE Wireless Issues"
date: 2016-11-04
forum: MINT
---

### Post by sesquipedalianman on 2016-11-04
I just purchased an Asus X555DA.  It has the rtl8821ae chipset in it.  Like I’ve been reading in the forums, I seem to have a similar issue as many.  My wireless network comes up, and stays up, but I lose connections.  When I run a continuous ping it will send about 50-60 packets, then drop 10, then come back up.  Then at times it will give me the “no buffer space available” message.  Dual boot back to Win10 & no issues with Wifi.
So far I’ve tried:
adding “options rtl8821ae  debug=0 disable_watchdog=N fwlps=N swlps=Y swenc=Y ips=N msi=0” to the a rrl8821.conf in /etc/modprobe.d
Updating drivers:
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms
Playing with antenna selection:
sudo modprobe -rv rtl8821be
sudo modprobe -v rtl8821ae ant_sel=2
& going back to ant 1

And combinations of all of the above both with provided and new drivers.

Nothing seems to change it.  About the only thing I haven’t done is open the box to see if I can rewire an antenna, but I’m not sure if this is an option on this chip.

What am I missing, or shall I just crack it open?

---

### Post by jeremy31 on 2016-11-04
See the wireless script link in my signature and post your results

---

### Post by sesquipedalianman on 2016-11-04
Slapping it inline.  Hopefully this isn't bad form.  This is the file with the stock driver

```
########## wireless info START ##########

Report from: 04 Nov 2016 20:42 EDT -0400

Booted last: 04 Nov 2016 00:00 EDT -0400

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

Xfce

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: XAVi Technologies Corp. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1b9a:2482]
	Kernel driver in use: rtl8821ae

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel modules: r8169

##### lsusb #############################

Bus 001 Device 004: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID b49a:04f2  
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rtl8821ae             225280  0
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              737280  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              565248  2 mac80211,rtlwifi
wmi                    20480  1 asus_wmi
video                  40960  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF1]>  
          inet addr:192.168.17.115  Bcast:192.168.17.255  Mask:255.255.255.0
          inet6 addr: fe80::7068:e75f:79d1:a2b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46810 (46.8 KB)  TX bytes:19827 (19.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlp1s0    IEEE 802.11abgn  ESSID:"deepthought"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'deepthought' [AN3]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.17.1    0.0.0.0         UG    600    0        0 wlp1s0
192.168.17.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0

##### resolv.conf #######################

nameserver 127.0.1.1
search earthlink.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root       853     1  1 20:42 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     deepthought
GENERAL.CON-UUID:                       a4663bb6-0bcd-4405-b810-e45d607b26aa
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a4663bb6-0bcd-4405-b810-e45d607b26aa | deepthought
IP4.ADDRESS[1]:                         192.168.17.115/24
IP4.GATEWAY:                            192.168.17.1
IP4.DNS[1]:                             208.67.222.222
IP4.DNS[2]:                             208.67.220.220
IP4.DNS[3]:                             207.69.188.186
IP4.DOMAIN[1]:                          earthlink.net
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.17.1
DHCP4.OPTION[10]:                       expiry = 1478392940
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.17.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.17.115
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = earthlink.net
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.17.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 208.67.222.222 208.67.220.220 207.69.188.186
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.17.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.17.1
IP6.ADDRESS[1]:                         fe80::7068:e75f:79d1:a2b3/64
IP6.GATEWAY:                            

SSID                    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
imwatching              <MAC 'imwatching' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
--                      <MAC '--' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
deepthought             <MAC 'deepthought' [AN3]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 
DIRECT-roku-490-0490AB  <MAC 'DIRECT-roku-490-0490AB' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
DIRECT-roku-060-5AF4C3  <MAC 'DIRECT-roku-060-5AF4C3' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
deepthought             <MAC 'deepthought' [AN3]>  Infra  6     2437 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/deepthought]] (600 root)
[connection] id=deepthought | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=deepthought
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

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

wlp1s0    Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/4.4.0-45-generic/updates/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     B9E24DCC76240A48AEEF94E
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.4.0-45-generic/updates/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     A96EBF28EBD4603749D5EC3
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-45-generic/updates/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     632F2E9C01BF2AC04D0F40A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

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

[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
int_clear: Y
ips: Y
msi: Y
swenc: N
swlps: N

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
blacklist r8169

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

[/etc/modprobe.d/ndiswrapper.conf]
alias wlan0 ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    6.646969] rtl8821ae 0000:01:00.0: enabling device (0000 -> 0003)
[    6.664252] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[    6.664264] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[    6.696712] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    6.697189] rtlwifi: rtlwifi: wireless switch is on
[    6.834909] rtl8821ae 0000:01:00.0 wlp1s0: renamed from wlan0
[    7.436698] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 3 times)
[   13.927132] wlp1s0: authenticate with <MAC 'deepthought' [AN3]>
[   13.933138] wlp1s0: send auth to <MAC 'deepthought' [AN3]> (try 1/3)
[   13.936055] wlp1s0: authenticated
[   13.937514] wlp1s0: associate with <MAC 'deepthought' [AN3]> (try 1/3)
[   13.942422] wlp1s0: RX AssocResp from <MAC 'deepthought' [AN3]> (capab=0x11 status=0 aid=6)
[   14.112767] wlp1s0: associated
[   14.112795] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready

########## wireless info END ############
```

Also grabbed one with the updated driver from the PPA

```
########## wireless info START ##########

Report from: 04 Nov 2016 20:27 EDT -0400

Booted last: 04 Nov 2016 00:00 EDT -0400

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

Xfce

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: XAVi Technologies Corp. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1b9a:2482]
	Kernel driver in use: rtl8821ae

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel modules: r8169

##### lsusb #############################

Bus 001 Device 004: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rtl8821ae             319488  0
btcoexist             180224  1 rtl8821ae
rtl_pci                40960  1 rtl8821ae
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8821ae
mac80211              737280  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              565248  2 mac80211,rtlwifi
wmi                    20480  1 asus_wmi
video                  40960  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF1]>  
          inet addr:192.168.17.115  Bcast:192.168.17.255  Mask:255.255.255.0
          inet6 addr: fe80::7068:e75f:79d1:a2b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3867197 (3.8 MB)  TX bytes:586128 (586.1 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlp1s0    IEEE 802.11abgn  ESSID:"deepthought"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'deepthought' [AN1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.17.1    0.0.0.0         UG    600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
192.168.17.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0

##### resolv.conf #######################

nameserver 127.0.1.1
search earthlink.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root       833     1  0 20:22 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     deepthought
GENERAL.CON-UUID:                       a4663bb6-0bcd-4405-b810-e45d607b26aa
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a4663bb6-0bcd-4405-b810-e45d607b26aa | deepthought
IP4.ADDRESS[1]:                         192.168.17.115/24
IP4.GATEWAY:                            192.168.17.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             208.67.222.222
IP4.DNS[2]:                             208.67.220.220
IP4.DNS[3]:                             207.69.188.186
IP4.DOMAIN[1]:                          earthlink.net
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.17.1
DHCP4.OPTION[10]:                       expiry = 1478391754
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.17.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.17.115
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = earthlink.net
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.17.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 208.67.222.222 208.67.220.220 207.69.188.186
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.17.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.17.1
IP6.ADDRESS[1]:                         fe80::7068:e75f:79d1:a2b3/64
IP6.GATEWAY:                            

SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
deepthought  <MAC 'deepthought' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 
deepthought  <MAC 'deepthought' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 
imwatching   <MAC 'imwatching' [AN3]>  Infra  6     2437 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
--           <MAC '--' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
--           <MAC '--' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
NETGEAR64    <MAC 'NETGEAR64' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        

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

[[/etc/NetworkManager/system-connections/deepthought]] (600 root)
[connection] id=deepthought | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=deepthought
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

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

wlp1s0    Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/4.4.0-45-generic/updates/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     B44D8007FC715E99771FA11
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.4.0-45-generic/updates/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8552A7BAFD0FCC2C41CF075
depends:        mac80211,rtlwifi
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-45-generic/updates/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     990116D31097F1C4C1F7006
depends:        mac80211,cfg80211
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

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

[rtl8821ae]
debug: 1
disable_watchdog: N
fwlps: Y
int_clear: Y
ips: Y
msi: Y
swenc: N
swlps: N

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
blacklist r8169

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

[/etc/modprobe.d/ndiswrapper.conf]
alias wlan0 ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    8.292572] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[    8.309782] rtl8821ae 0000:01:00.0: enabling device (0000 -> 0003)
[    8.353621] Using firmware rtlwifi/rtl8821aefw.bin
[    8.353796] rtlwifi: channel plan 0x7f
[    8.353798] rtlwifi: country code 13
[    8.384922] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.385619] rtlwifi: wireless switch is on
[    8.538184] rtl8821ae 0000:01:00.0 wlp1s0: renamed from wlan0
[    9.277996] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    9.394974] rtl8821ae:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070304 .
[    9.536819] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[    9.661542] rtl8821ae:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070604 .
[   15.626301] wlp1s0: authenticate with <MAC 'deepthought' [AN1]>
[   15.630966] wlp1s0: send auth to <MAC 'deepthought' [AN1]> (try 1/3)
[   15.643006] wlp1s0: authenticated
[   15.645081] wlp1s0: associate with <MAC 'deepthought' [AN1]> (try 1/3)
[   15.649831] wlp1s0: RX AssocResp from <MAC 'deepthought' [AN1]> (capab=0x11 status=0 aid=10)
[   15.651102] wlp1s0: associated
[   15.651120] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready

########## wireless info END ############
```

---

### Post by howefield on 2016-11-05
Thread moved to the "MINT" forum.

---

### Post by jeremy31 on 2016-11-06
Sounds like a power management issue ```
echo "options rtl8821ae fwlps=N" | sudo tee -a /etc/modprobe.d/rtl8821ae.conf
```

Reboot

---

### Post by dcheek2 on 2017-01-28
I also have an asus x555 with a similar experience to OP, wireless works great on Win10, but fresh install of yakkety times out after a few seconds. I have tried all the above with no luck, anything else missing?

---

### Post by wildmanne39 on 2017-01-28
Please start your own thread in the appropriate section of the forum, using a descriptive title.

---

