---
title: "AC1200 Dual-Band USB 3.0 Wifi Adapter"
date: 2018-12-18
forum: MINT
---

### Post by leona on 2018-12-18
Hi
I'm using Mint 18.3
I have the above adaptor
I've get the drivers from github
the adaptor starts up ok
but after a period of inactivity it seems to loose internet access, the status shows online, but can't access websites or emails.
Unplugging and reinserting the adaptor seems to fix the problem.
This problem only seems to happen on my partners account, rather than mine.
This didn't happen with a previous adaptor, so this must be the cause?
Any idea how I can diagnose and fix this?  It annoys my partner and causes me grief, so would like to resolve it.
Thanks
Leona.

---

### Post by jeremy31 on 2018-12-18
Moved to Mint, see the wireless script link in my signature and post results

---

### Post by leona on 2018-12-19
Thank you @jeremy31 didn't know there was a mint section so that's good.

the results from the script are in.....
```


########## wireless info START ##########

Report from: 19 Dec 2018 21:39 GMT +0000

Booted last: 19 Dec 2018 00:00 GMT +0000

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	LinuxMint
Description:	Linux Mint 18.3 Sylvia
Release:	18.3
Codename:	sylvia

##### kernel ############################

Linux 4.8.0-53-generic #56~16.04.1-Ubuntu SMP Tue May 16 01:18:56 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7756]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 3207:0300  
Bus 001 Device 004: ID 047d:2048 Kensington Orbit Trackball with Scroll Ring
Bus 001 Device 007: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 005: ID 05a9:2649 OmniVision Technologies, Inc. 
Bus 001 Device 003: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

cfg80211              581632  1 88x2bu
wmi                    16384  0

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
4: wlx<IF from MAC [IF2]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlx<IF from MAC [IF2]>' [IF2]> brd <MAC address>
    inet 192.168.0.2/24 brd 192.168.0.255 scope global wlx<IF from MAC [IF2]>
       valid_lft forever preferred_lft forever
    inet6 fe80::838d:247f:d4df:bf6d/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11AC  ESSID:"MYSSID5G"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC 'MYSSID5G' [AC7]>   
          Bit Rate:867 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/100  Signal level=40/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

default via 192.168.0.1 dev wlx<IF from MAC [IF2]>  proto static  metric 600 
169.254.0.0/16 dev wlx<IF from MAC [IF2]>  scope link  metric 1000 
192.168.0.0/24 dev wlx<IF from MAC [IF2]>  proto kernel  scope link  src 192.168.0.2  metric 600 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']
nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       920     1  0 17:45 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11ac NIC
GENERAL.DRIVER:                         rtl88x2bu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto MYSSID5G
GENERAL.CON-UUID:                       73c785ee-fa2b-4b9f-a891-cf91081a609a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     867 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8c17eeb0-a5c3-4da9-b52d-347dbcf0e2aa | Auto MYSSID
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   73c785ee-fa2b-4b9f-a891-cf91081a609a | Auto MYSSID5G
IP4.ADDRESS[1]:                         192.168.0.2/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             1.1.1.1
IP4.DNS[2]:                             1.0.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1545255398
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.2
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 1.1.1.1 1.0.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::838d:247f:d4df:bf6d/64
IP6.GATEWAY:                            

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
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/enp2s0
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

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
MYSSID      <MAC 'MYSSID' [AC5]>  Infra  10    2457 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2              no        
--               <MAC '' [AC6]>  Infra  10    2457 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2              no        
MYSSID5G    <MAC 'MYSSID5G' [AC7]>  Infra  36    5180 MHz  54 Mbit/s  61      &#9602;&#9604;&#9606;_  WPA2              yes     * 
BTWifi-with-FON  <MAC 'BTWifi-with-FON' [AC9]>  Infra  7     2442 MHz  54 Mbit/s  35      &#9602;&#9604;__  --                no        
BTHub4-JFJ9      <MAC 'BTHub4-JFJ9' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2         no        
BTWifi-X         <MAC 'BTWifi-X' [AC4]>  Infra  7     2442 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
BTWifi-with-FON  <MAC 'BTWifi-with-FON' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  30      &#9602;___  --                no        
BTHub5-2TWZ      <MAC 'BTHub5-2TWZ' [AC8]>  Infra  7     2442 MHz  54 Mbit/s  30      &#9602;___  WPA2              no        
BTWifi-X         <MAC 'BTWifi-X' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2 802.1X  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Auto MYSSID]] (600 root)
[connection] id=Auto MYSSID | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MYSSID
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto MYSSID-fe6b20a8-b665-475d-962a-f5b62ccf185e]] (600 root)
[connection] id=Auto MYSSID | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MYSSID
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto MYSSID]] (600 root)
[connection] id=Auto MYSSID | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MYSSID
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto MYSSID-8c17eeb0-a5c3-4da9-b52d-347dbcf0e2aa]] (600 root)
[connection] id=Auto MYSSID | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=MYSSID
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto MYSSID5G]] (600 root)
[connection] id=Auto MYSSID5G | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=MYSSID5G
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp2s0    no frequency information.

wlx<IF from MAC [IF2]>  32 channels in total; available frequencies :
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
          Current Frequency:5.18 GHz (Channel 36)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:5.18 GHz (Channel 36)

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.8.0-53-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-53-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[    5.193209] rtl88x2bu 3-4:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[    5.345308] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    5.475037] r8169 0000:02:00.0 enp2s0: link down
[    5.475085] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    5.483802] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[   14.539937] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[13848.514053] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready
[13865.760228] rtl88x2bu 3-4:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[13865.786637] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[13874.546933] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2018-12-19
I would disable Network Managers ability to enable wifi power management with
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by leona on 2018-12-21
Oh nice idea, ya that makes sense, thank you will give that a try.

---

### Post by leona on 2019-01-03
Marking as solved as haven't seen the problem since, thank you.

---

### Post by leona on 2019-01-04
Spoke too soon, not solved, it died on my tonight, lists all the networks, but will not connect to any of them, have to pull the adaptor and reinsert, only seems to do this if computer on for some time.
Have updated to Mint 19.1 since I posted this.

---

### Post by jeremy31 on 2019-01-04
Post results for ```
modinfo -p 88x2bu
```

---

### Post by leona on 2019-01-10
Output of 
```
modinfo -p 88x2bu
```
is 

```
rtw_ips_mode:The default IPS mode (int)
rtw_lps_level:The default LPS level (int)
rtw_usb_rxagg_mode: (int)
rtw_dynamic_agg_enable: (int)
rtw_drv_log_level:set log level when insert driver module, default log level is _DRV_INFO_ = 4 (uint)
rtw_tx_bw_mode:The max tx bw for 2.4G and 5G. format is the same as rtw_bw_mode (uint)
rtw_rx_ampdu_sz_limit_1ss:RX AMPDU size limit for 1SS link of each BW, 0xFF: no limitation (array of uint)
rtw_rx_ampdu_sz_limit_2ss:RX AMPDU size limit for 2SS link of each BW, 0xFF: no limitation (array of uint)
rtw_rx_ampdu_sz_limit_3ss:RX AMPDU size limit for 3SS link of each BW, 0xFF: no limitation (array of uint)
rtw_rx_ampdu_sz_limit_4ss:RX AMPDU size limit for 4SS link of each BW, 0xFF: no limitation (array of uint)
rtw_vht_enable: (int)
rtw_vht_rx_mcs_map:VHT RX MCS map (uint)
rtw_rf_config: (int)
rtw_country_code:The default country code (in alpha2) (charp)
rtw_channel_plan:The default chplan ID when rtw_alpha2 is not specified or valid (int)
rtw_excl_chs:exclusive channel array (array of uint)
rtw_btcoex_enable:BT co-existence on/off, 0:off, 1:on, 2:by efuse (int)
rtw_ant_num:Antenna number setting, 0:by efuse (int)
rtw_force_igi_lb:force IGI low-bound, 0:no specified (int)
rtw_qos_opt_enable: (int)
ifname:The default name to allocate for first interface (charp)
if2name:The default name to allocate for second interface (charp)
rtw_pwrtrim_enable: (int)
rtw_initmac: (charp)
rtw_special_rf_path: (int)
rtw_chip_version: (int)
rtw_rfintfs: (int)
rtw_lbkmode: (int)
rtw_network_mode: (int)
rtw_channel: (int)
rtw_mp_mode: (int)
rtw_wmm_enable: (int)
rtw_vrtl_carrier_sense: (int)
rtw_vcs_type: (int)
rtw_busy_thresh: (int)
rtw_ht_enable: (int)
rtw_bw_mode: (int)
rtw_ampdu_enable: (int)
rtw_rx_stbc: (int)
rtw_ampdu_amsdu: (int)
rtw_lowrate_two_xmit: (int)
rtw_power_mgnt: (int)
rtw_smart_ps: (int)
rtw_low_power: (int)
rtw_wifi_spec: (int)
rtw_full_ch_in_p2p_handshake: (int)
rtw_antdiv_cfg: (int)
rtw_antdiv_type: (int)
rtw_drv_ant_band_switch: (int)
rtw_switch_usb_mode: (int)
rtw_enusbss: (int)
rtw_hwpdn_mode: (int)
rtw_hwpwrp_detect: (int)
rtw_hw_wps_pbc: (int)
rtw_check_hw_status: (int)
rtw_max_roaming_times:The max roaming times to try (uint)
rtw_mc2u_disable: (int)
rtw_80211d:Enable 802.11d mechanism (int)
rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
rtw_adaptivity_en:0:disable, 1:enable (uint)
rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
rtw_adaptivity_dml:0:disable, 1:enable (uint)
rtw_adaptivity_dc_backoff:DC backoff for Adaptivity (uint)
rtw_adaptivity_th_l2h_ini:th_l2h_ini for Adaptivity (int)
rtw_adaptivity_th_edcca_hl_diff:th_edcca_hl_diff for Adaptivity (int)
rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
rtw_RFE_type:default init value:64 (uint)
rtw_powertracking_type:default init value:64 (uint)
rtw_GLNA_type:default init value:0 (uint)
rtw_TxBBSwing_2G:default init value:0xFF (uint)
rtw_TxBBSwing_5G:default init value:0xFF (uint)
rtw_OffEfuseMask:default open Efuse Mask value:0 (uint)
rtw_FileMaskEfuse:default drv Mask Efuse value:0 (uint)
rtw_rxgain_offset_2g:default RF Gain 2G Offset value:0 (uint)
rtw_rxgain_offset_5gl:default RF Gain 5GL Offset value:0 (uint)
rtw_rxgain_offset_5gh: (uint)
rtw_rxgain_offset_5gm:default RF Gain 5GM Offset value:0 (uint)
rtw_pll_ref_clk_sel:force pll_ref_clk_sel, 0xF:use autoload value (uint)
rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
rtw_target_tx_pwr_2g_a:2.4G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_2g_b:2.4G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_2g_c:2.4G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_2g_d:2.4G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_5g_a:5G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_5g_b:5G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_5g_c:5G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_target_tx_pwr_5g_d:5G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
rtw_phy_file_path:The path of phy parameter (charp)
rtw_load_phy_file:PHY File Bit Map (int)
rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
rtw_en_napi: (int)
rtw_en_gro: (int)
rtw_iqk_fw_offload: (int)

```

---

### Post by jeremy31 on 2019-01-11
```
echo "options 88x2bu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/88x2bu.conf
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

Reboot

---

