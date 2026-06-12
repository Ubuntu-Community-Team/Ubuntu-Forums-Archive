---
title: "WLAN-Stick DIGITUS DN-7045; Problems; USB 0bda:8176 Realtec RTL8188CU"
date: 2018-09-07
forum: MINT
---

### Post by jonny62 on 2018-09-07
Hello,
need help to start WLAN-stick on Linux Mint 18.3 Cinnamon 64-bit
tried a lot internet information but didn't work it out to work

[https://ubuntuforums.org/showthread.php?t=2352681&page=2](https://ubuntuforums.org/showthread.php?t=2352681&page=2)

any idea?
Thanks!

```


########## wireless info START ##########

Report from: 07 Sep 2018 10:31 CEST +0200

Booted last: 07 Sep 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 18.3 Sylvia
Release:    18.3
Codename:    sylvia

##### kernel ############################

Linux 4.15.0-33-generic #36~16.04.1-Ubuntu SMP Wed Aug 15 17:21:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7a70]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04a9:1801 Canon, Inc. 
Bus 001 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 001 Device 002: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard G230
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 006: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

8192cu                569344  0
cfg80211              622592  1 8192cu
intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  0
wmi                    24576  2 intel_wmi_thunderbolt,mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback 

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          inet addr:192.168.178.41  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::1386:8b00:5dc2:24af/64 Scope:Link
          inet6 addr: 2a02:908:8a4:6fc0:e073:6c4d:fc5:a49f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4724 errors:0 dropped:2 overruns:0 frame:0
          TX packets:4292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4375035 (4.3 MB)  TX bytes:594065 (594.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86027 (86.0 KB)  TX bytes:86027 (86.0 KB)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:15 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp1s0    no wireless extensions.

lo        no wireless extensions.

wlx<IF from MAC [IF2]>  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.178.0   0.0.0.0         255.255.255.0   U     100    0        0 enp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       977     1  0 10:19 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ethernet connection 1
GENERAL.CON-UUID:                       4fdc9a79-21a7-4379-ae3e-66ae4d3d6f66
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4fdc9a79-21a7-4379-ae3e-66ae4d3d6f66 | Ethernet connection 1
IP4.ADDRESS[1]:                         192.168.178.41/24
IP4.GATEWAY:                            192.168.178.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.178.1
IP6.ADDRESS[1]:                         2a02:908:8a4:6fc0:e073:6c4d:fc5:a49f/64
IP6.ADDRESS[2]:                         fe80::1386:8b00:5dc2:24af/64
IP6.GATEWAY:                            fe80::464e:6dff:fe2b:92d8
IP6.ROUTE[1]:                           dst = 2a02:908:8a4:6fc0::/59, nh = fe80::464e:6dff:fe2b:92d8, mt = 100
IP6.ROUTE[2]:                           dst = 2a02:908:8a4:6fc0::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fd00::464e:6dff:fe2b:92d8

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8192cu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.0/net/wlx<IF from MAC [IF2]>
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8d8cb5b2-3039-4a80-8145-09316fb9ac36 | WLAN-FINDHORN

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
devolo-e38     <MAC 'devolo-e38' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2      no        
WLAN-FINDHORN  <MAC 'WLAN-FINDHORN' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2      no        

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

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/WLAN-FINDHORN]] (600 root)
[connection] id=WLAN-FINDHORN | type=wifi | permissions=user:norbert:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=WLAN-FINDHORN
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (5725 - 5875 @ 80), (N/A, 13), (N/A)
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp1s0    no frequency information.

lo        no frequency information.

wlx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

enp1s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'WLAN-FINDHORN' [AC1]>
                    ESSID:"WLAN-FINDHORN"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=44/100  

##### module infos ######################

[8192cu]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/8192cu.ko
version:        v4.0.2_9000.20130911
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     6AD5C04A6CC39FDA305AE8F
depends:        cfg80211
retpoline:      Y
name:           8192cu
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)

[cfg80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     AFB624FD5B16A8AA59A9CF7
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[8192cu]
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 65
rtw_chip_version: 0
rtw_enusbss: 0
rtw_force_iol: N
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_mac_phy_mode: 0
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 0
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_special_rf_path: 0
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

rtl8xxxu

##### modprobe options ##################

[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

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
blacklist rtl8192cu
blacklist rtl8192cu
blacklist rtl8xxxu

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
install rtl8xxxu /bin/false

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

mount -t ext4 /dev/sdb3 /media/norbert/DATA

mount --bind /media/norbert/DATA/Bilder  /home/norbert/Bilder
mount --bind /media/norbert/DATA/Videos  /home/norbert/Videos
mount --bind /media/norbert/DATA/Musik  /home/norbert/Musik

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    4.151717] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    4.214607] r8169 0000:01:00.0 enp1s0: link down
[    4.214688] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    4.216299] r8169 0000:01:00.0 enp1s0: link down
[    5.826751] r8169 0000:01:00.0 enp1s0: link up
[    5.826759] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
[  198.259047] r8169 0000:01:00.0 enp1s0: link down
[  203.936114] rtl8192cu 1-10:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[  203.965129] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 4 times)
[  330.269217] r8169 0000:01:00.0 enp1s0: link up

########## wireless info END ############


```

---

### Post by jeremy31 on 2018-09-07
Moved to Mint

---

### Post by chili555 on 2018-09-08
Is this helpful?  [https://askubuntu.com/questions/1073355/how-to-remove-last-installed-driver](https://askubuntu.com/questions/1073355/how-to-remove-last-installed-driver)

> thank you so much. It works now. You just solved my both problems at once! 

---

### Post by jonny62 on 2018-09-08
no, was not helpful; still no connection
I think the setup should reset and start install the driver from the very begin again
any help?

```

########## wireless info START ##########

Report from: 08 Sep 2018 17:32 CEST +0200

Booted last: 08 Sep 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 18.3 Sylvia
Release:    18.3
Codename:    sylvia

##### kernel ############################

Linux 4.15.0-33-generic #36~16.04.1-Ubuntu SMP Wed Aug 15 17:21:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7a70]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04a9:1801 Canon, Inc. 
Bus 001 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 001 Device 002: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard G230
Bus 001 Device 006: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 005: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  0
wmi                    24576  2 intel_wmi_thunderbolt,mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback 

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          inet addr:192.168.178.41  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::1386:8b00:5dc2:24af/64 Scope:Link
          inet6 addr: 2a02:908:8a9:94e0:32be:b8e2:a665:7610/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:419357 (419.3 KB)  TX bytes:167025 (167.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26733 (26.7 KB)  TX bytes:26733 (26.7 KB)

##### iwconfig ##########################

enp1s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.178.0   0.0.0.0         255.255.255.0   U     100    0        0 enp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       970     1  0 17:30 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ethernet connection 1
GENERAL.CON-UUID:                       4fdc9a79-21a7-4379-ae3e-66ae4d3d6f66
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4fdc9a79-21a7-4379-ae3e-66ae4d3d6f66 | Ethernet connection 1
IP4.ADDRESS[1]:                         192.168.178.41/24
IP4.GATEWAY:                            192.168.178.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.178.1
IP6.ADDRESS[1]:                         2a02:908:8a9:94e0:32be:b8e2:a665:7610/64
IP6.ADDRESS[2]:                         fe80::1386:8b00:5dc2:24af/64
IP6.GATEWAY:                            fe80::464e:6dff:fe2b:92d8
IP6.ROUTE[1]:                           dst = 2a02:908:8a9:94e0::/59, nh = fe80::464e:6dff:fe2b:92d8, mt = 100
IP6.ROUTE[2]:                           dst = 2a02:908:8a9:94e0::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fd00::464e:6dff:fe2b:92d8

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

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/WLAN-FINDHORN]] (600 root)
[connection] id=WLAN-FINDHORN | type=wifi | permissions=user:norbert:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WLAN-FINDHORN
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp1s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp1s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

rtl8xxxu

##### modprobe options ##################

[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

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
blacklist rtl8192cu
blacklist rtl8192cu
blacklist rtl8xxxu
blacklist rtl8192cu

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

mount -t ext4 /dev/sdb3 /media/norbert/DATA

mount --bind /media/norbert/DATA/Bilder  /home/norbert/Bilder
mount --bind /media/norbert/DATA/Videos  /home/norbert/Videos
mount --bind /media/norbert/DATA/Musik  /home/norbert/Musik

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    3.449497] systemd[1]: Started Trigger resolvconf update for networkd DNS.
[    4.201359] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    4.266615] r8169 0000:01:00.0 enp1s0: link down (repeated 2 times)
[    4.266699] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    5.994414] r8169 0000:01:00.0 enp1s0: link up
[    5.994422] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready

########## wireless info END ############

```

---

### Post by chili555 on 2018-09-08
> I think the setup should reset and start install the driver from the very begin againI don't believe so.

Please try:```
sudo rm /etc/modprobe.d/8192cu-disable-power-management.conf
sudo nano /etc/modprobe.d/blacklist.conf
```Change the last several lines from this:```
<...>
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rtl8192cu
blacklist rtl8192cu
blacklist rtl8xxxu
blacklist rtl8192cu

```To this:```
<...>
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rtl8192cu

```Proofread carefully twice, save (Ctrl+o followed by Enter) and exit (Ctrl+x) the text editor.

Reboot and tell us if the wireless is working.

---

### Post by jonny62 on 2018-09-08
wireless starts to work but no connection established
two times asking for key and then disconnecting

```


########## wireless info START ##########

Report from: 08 Sep 2018 22:59 CEST +0200

Booted last: 08 Sep 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 18.3 Sylvia
Release:    18.3
Codename:    sylvia

##### kernel ############################

Linux 4.15.0-33-generic #36~16.04.1-Ubuntu SMP Wed Aug 15 17:21:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7a70]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04a9:1801 Canon, Inc. 
Bus 001 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 001 Device 002: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard G230
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 006: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

intel_wmi_thunderbolt    16384  0
rtl8xxxu              122880  0
mac80211              778240  1 rtl8xxxu
cfg80211              622592  1 mac80211
mxm_wmi                16384  0
wmi                    24576  2 intel_wmi_thunderbolt,mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback 

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          inet addr:192.168.178.41  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: 2a02:908:8a9:94e0:32be:b8e2:a665:7610/64 Scope:Global
          inet6 addr: fe80::1386:8b00:5dc2:24af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:490 errors:0 dropped:3 overruns:0 frame:0
          TX packets:598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:166200 (166.2 KB)  TX bytes:164729 (164.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16543 (16.5 KB)  TX bytes:16543 (16.5 KB)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2215 (2.2 KB)  TX bytes:5195 (5.1 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.178.0   0.0.0.0         255.255.255.0   U     100    0        0 enp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       950     1  0 22:56 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ethernet connection 1
GENERAL.CON-UUID:                       4fdc9a79-21a7-4379-ae3e-66ae4d3d6f66
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4fdc9a79-21a7-4379-ae3e-66ae4d3d6f66 | Ethernet connection 1
IP4.ADDRESS[1]:                         192.168.178.41/24
IP4.GATEWAY:                            192.168.178.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.178.1
IP6.ADDRESS[1]:                         2a02:908:8a9:94e0:32be:b8e2:a665:7610/64
IP6.ADDRESS[2]:                         fe80::1386:8b00:5dc2:24af/64
IP6.GATEWAY:                            fe80::464e:6dff:fe2b:92d8
IP6.ROUTE[1]:                           dst = 2a02:908:8a9:94e0::/59, nh = fe80::464e:6dff:fe2b:92d8, mt = 100
IP6.ROUTE[2]:                           dst = 2a02:908:8a9:94e0::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fd00::464e:6dff:fe2b:92d8

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 4.15.0-33-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.0/net/wlx<IF from MAC [IF2]>
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   dfa40c43-4dfc-4620-8499-397e0178e05e | WLAN-FINDHORN

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
WLAN-FINDHORN  <MAC 'WLAN-FINDHORN' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  30      &#9602;___  WPA2      no        

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

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/WLAN-FINDHORN]] (600 root)
[connection] id=WLAN-FINDHORN | type=wifi | permissions=user:norbert:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=WLAN-FINDHORN
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (5725 - 5875 @ 80), (N/A, 13), (N/A)
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

wlx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'WLAN-FINDHORN' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"WLAN-FINDHORN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ab441bd4f
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8723bu_bt.bin
firmware:       rtlwifi/rtl8723bu_nic.bin
firmware:       rtlwifi/rtl8192eu_nic.bin
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@gmail.com>
srcversion:     E7E78FAA920143C9B0CB35A
depends:        mac80211
retpoline:      Y
intree:         Y
name:           rtl8xxxu
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)
parm:           dma_aggregation:Enable DMA packet aggregation (bool)
parm:           dma_agg_timeout:Set DMA aggregation timeout (range 1-127) (int)
parm:           dma_agg_pages:Set DMA aggregation pages (range 1-127, 0 to disable) (int)

[mac80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     AFB624FD5B16A8AA59A9CF7
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_pages: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_aggregation: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_timeout: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

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

rtl8xxxu

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
blacklist rtl8192cu

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

mount -t ext4 /dev/sdb3 /media/norbert/DATA

mount --bind /media/norbert/DATA/Bilder  /home/norbert/Bilder
mount --bind /media/norbert/DATA/Videos  /home/norbert/Videos
mount --bind /media/norbert/DATA/Musik  /home/norbert/Musik

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    4.216262] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    4.274603] r8169 0000:01:00.0 enp1s0: link down (repeated 2 times)
[    4.274734] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    5.907733] r8169 0000:01:00.0 enp1s0: link up
[    5.907739] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
[   69.038639] usb 1-10: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[   69.038768] usb 1-10: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   70.519510] rtl8xxxu 1-10:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[   70.555164] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[  120.985059] wlx<IF from MAC [IF2]>: authenticate with <MAC 'WLAN-FINDHORN' [AC1]>
[  120.990922] wlx<IF from MAC [IF2]>: send auth to <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  120.995836] wlx<IF from MAC [IF2]>: authenticated
[  120.996784] wlx<IF from MAC [IF2]>: associate with <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  121.003339] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'WLAN-FINDHORN' [AC1]> (capab=0x431 status=0 aid=5)
[  121.003991] usb 1-10: rtl8xxxu_bss_info_changed: HT supported
[  121.004593] wlx<IF from MAC [IF2]>: associated
[  125.006668] wlx<IF from MAC [IF2]>: disassociated from <MAC 'WLAN-FINDHORN' [AC1]> (Reason: 2=PREV_AUTH_NOT_VALID)
[  130.905344] wlx<IF from MAC [IF2]>: authenticate with <MAC 'WLAN-FINDHORN' [AC1]>
[  130.911605] wlx<IF from MAC [IF2]>: send auth to <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  130.914514] wlx<IF from MAC [IF2]>: authenticated
[  130.917097] wlx<IF from MAC [IF2]>: associate with <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  130.922918] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'WLAN-FINDHORN' [AC1]> (capab=0x431 status=0 aid=5)
[  130.923460] usb 1-10: rtl8xxxu_bss_info_changed: HT supported
[  130.924061] wlx<IF from MAC [IF2]>: associated
[  132.938970] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[  136.934189] wlx<IF from MAC [IF2]>: disassociated from <MAC 'WLAN-FINDHORN' [AC1]> (Reason: 2=PREV_AUTH_NOT_VALID)
[  137.929535] wlx<IF from MAC [IF2]>: authenticate with <MAC 'WLAN-FINDHORN' [AC1]>
[  137.935047] wlx<IF from MAC [IF2]>: send auth to <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  137.941087] wlx<IF from MAC [IF2]>: authenticated
[  137.941257] wlx<IF from MAC [IF2]>: associate with <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  137.955265] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'WLAN-FINDHORN' [AC1]> (capab=0x431 status=0 aid=5)
[  137.955816] usb 1-10: rtl8xxxu_bss_info_changed: HT supported
[  137.956419] wlx<IF from MAC [IF2]>: associated
[  165.030589] wlx<IF from MAC [IF2]>: deauthenticating from <MAC 'WLAN-FINDHORN' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############

```

---

### Post by chili555 on 2018-09-08
> Cell 01 - Address: <MAC 'WLAN-FINDHORN' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    [COLOR="#FF0000"]Quality=26/70 [/COLOR] Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"WLAN-FINDHORN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ab441bd4f
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
Wow! How far from the router are you?

Is the router set to auto channel select, by any chance? Please check here:  [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection) I recommend a fixed channel; either 1, 6 or 11.

---

### Post by jonny62 on 2018-09-09
distance to the router is about 10m diagonal to the house and one floor
I changed the wifi channel to fixed 1 and extended the USB-WLAN by 1m adaptor wire
perfect...now there is a connection to the router
but: now IP-address
there is a connection to the router so I can manage the setup of the fritzbox
but no connection to the internet

today evening: connection to the internet but still no IP-address shown on setup page router?

```

########## wireless info START ##########

Report from: 09 Sep 2018 10:20 CEST +0200

Booted last: 09 Sep 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 18.3 Sylvia
Release:    18.3
Codename:    sylvia

##### kernel ############################

Linux 4.15.0-33-generic #36~16.04.1-Ubuntu SMP Wed Aug 15 17:21:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7a70]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04a9:1801 Canon, Inc. 
Bus 001 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 001 Device 002: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard G230
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 018: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

12: phy12: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

intel_wmi_thunderbolt    16384  0
rtl8xxxu              122880  0
mac80211              778240  1 rtl8xxxu
cfg80211              622592  1 mac80211
mxm_wmi                16384  0
wmi                    24576  2 intel_wmi_thunderbolt,mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback 

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          inet addr:192.168.178.41  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: 2a02:908:8a9:94e0:32be:b8e2:a665:7610/64 Scope:Global
          inet6 addr: fe80::1386:8b00:5dc2:24af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7279 errors:0 dropped:478 overruns:0 frame:0
          TX packets:5603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6550928 (6.5 MB)  TX bytes:908176 (908.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:177082 (177.0 KB)  TX bytes:177082 (177.0 KB)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          inet6 addr: 2a02:908:8a9:94e0:7eec:c166:53de:eb71/64 Scope:Global
          inet6 addr: fe80::df43:2d2d:4fbf:83de/64 Scope:Link
          inet6 addr: 2a02:908:8a9:94e0:e4d7:aef4:2e56:e45d/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2825 errors:0 dropped:356 overruns:0 frame:0
          TX packets:868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:976017 (976.0 KB)  TX bytes:126363 (126.3 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11  ESSID:"WLAN-FINDHORN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'WLAN-FINDHORN' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.178.0   0.0.0.0         255.255.255.0   U     100    0        0 enp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       962     1  0 09:54 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ethernet connection 1
GENERAL.CON-UUID:                       4fdc9a79-21a7-4379-ae3e-66ae4d3d6f66
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4fdc9a79-21a7-4379-ae3e-66ae4d3d6f66 | Ethernet connection 1
IP4.ADDRESS[1]:                         192.168.178.41/24
IP4.GATEWAY:                            192.168.178.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.178.1
IP6.ADDRESS[1]:                         2a02:908:8a9:94e0:32be:b8e2:a665:7610/64
IP6.ADDRESS[2]:                         fe80::1386:8b00:5dc2:24af/64
IP6.GATEWAY:                            fe80::464e:6dff:fe2b:92d8
IP6.ROUTE[1]:                           dst = 2a02:908:8a9:94e0::/59, nh = fe80::464e:6dff:fe2b:92d8, mt = 100
IP6.ROUTE[2]:                           dst = 2a02:908:8a9:94e0::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fd00::464e:6dff:fe2b:92d8

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 4.15.0-33-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WLAN-FINDHORN
GENERAL.CON-UUID:                       dfa40c43-4dfc-4620-8499-397e0178e05e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   dfa40c43-4dfc-4620-8499-397e0178e05e | WLAN-FINDHORN
IP6.ADDRESS[1]:                         2a02:908:8a9:94e0:e4d7:aef4:2e56:e45d/64
IP6.ADDRESS[2]:                         2a02:908:8a9:94e0:7eec:c166:53de:eb71/64
IP6.ADDRESS[3]:                         fe80::df43:2d2d:4fbf:83de/64
IP6.GATEWAY:                            fe80::464e:6dff:fe2b:92d8
IP6.ROUTE[1]:                           dst = 2a02:908:8a9:94e0::/59, nh = fe80::464e:6dff:fe2b:92d8, mt = 600
IP6.DNS[1]:                             fd00::464e:6dff:fe2b:92d8

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
WLAN-FINDHORN  <MAC 'WLAN-FINDHORN' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       yes     * 
devolo-e38     <MAC 'devolo-e38' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  20      &#9602;___  WPA2       no        
QUINTUS2016    <MAC 'QUINTUS2016' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  14      &#9602;___  WPA1 WPA2  no        
NSA-Spider     <MAC 'NSA-Spider' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  10      &#9602;___  WPA2       no        
devolo-b2c     <MAC 'devolo-b2c' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  4       ____  WPA2       no        

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

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/WLAN-FINDHORN]] (600 root)
[connection] id=WLAN-FINDHORN | type=wifi | permissions=user:norbert:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=WLAN-FINDHORN
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (5725 - 5875 @ 80), (N/A, 13), (N/A)
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

wlx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'WLAN-FINDHORN' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"WLAN-FINDHORN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000003b50793
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'devolo-e38' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"devolo-e38"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001d0bac54d4c2
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'FRITZ!Box Fon WLAN 7390' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7390"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000133d19d80
                    Extra: Last beacon: 2292ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (0) :
                        Authentication Suites (0) :
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (0) :
                        Authentication Suites (0) :
          Cell 04 - Address: <MAC 'devolo-b2c' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"devolo-b2c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000213ae76b9cc7
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'QUINTUS2016' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"QUINTUS2016"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012776516180
                    Extra: Last beacon: 2676ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'NSA-Spider' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"NSA-Spider"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001005b503180
                    Extra: Last beacon: 828ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8723bu_bt.bin
firmware:       rtlwifi/rtl8723bu_nic.bin
firmware:       rtlwifi/rtl8192eu_nic.bin
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@gmail.com>
srcversion:     E7E78FAA920143C9B0CB35A
depends:        mac80211
retpoline:      Y
intree:         Y
name:           rtl8xxxu
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)
parm:           dma_aggregation:Enable DMA packet aggregation (bool)
parm:           dma_agg_timeout:Set DMA aggregation timeout (range 1-127) (int)
parm:           dma_agg_pages:Set DMA aggregation pages (range 1-127, 0 to disable) (int)

[mac80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     AFB624FD5B16A8AA59A9CF7
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_pages: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_aggregation: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_timeout: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

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

rtl8xxxu

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
blacklist rtl8192cu

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

mount -t ext4 /dev/sdb3 /media/norbert/DATA

mount --bind /media/norbert/DATA/Bilder  /home/norbert/Bilder
mount --bind /media/norbert/DATA/Videos  /home/norbert/Videos
mount --bind /media/norbert/DATA/Musik  /home/norbert/Musik

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  536.436906] usb 1-10: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[  537.917779] rtl8xxxu 1-10:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[  537.944396] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[  542.557370] usb 1-10: rtl8xxxu_active_to_lps: RX poll timed out (0x05f8)
[  542.562417] usb 1-10: rtl8xxxu_active_to_emu: Disabling MAC timed out
[  543.038475] usb 1-10: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[  543.038547] usb 1-10: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[  544.519188] rtl8xxxu 1-10:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[  544.542753] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[  585.368483] wlx<IF from MAC [IF2]>: authenticate with <MAC 'WLAN-FINDHORN' [AC1]>
[  585.376485] wlx<IF from MAC [IF2]>: send auth to <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  585.380118] wlx<IF from MAC [IF2]>: authenticated
[  585.382879] wlx<IF from MAC [IF2]>: associate with <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  585.388411] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'WLAN-FINDHORN' [AC1]> (capab=0x431 status=0 aid=6)
[  585.388966] usb 1-10: rtl8xxxu_bss_info_changed: HT supported
[  585.389941] wlx<IF from MAC [IF2]>: associated
[  589.392281] wlx<IF from MAC [IF2]>: disassociated from <MAC 'WLAN-FINDHORN' [AC1]> (Reason: 2=PREV_AUTH_NOT_VALID)
[  592.739869] wlx<IF from MAC [IF2]>: authenticate with <MAC 'WLAN-FINDHORN' [AC1]>
[  592.745353] wlx<IF from MAC [IF2]>: send auth to <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  592.748158] wlx<IF from MAC [IF2]>: authenticated
[  592.751098] wlx<IF from MAC [IF2]>: associate with <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  592.759145] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'WLAN-FINDHORN' [AC1]> (capab=0x431 status=0 aid=6)
[  592.759722] usb 1-10: rtl8xxxu_bss_info_changed: HT supported
[  592.760332] wlx<IF from MAC [IF2]>: associated
[  596.762399] wlx<IF from MAC [IF2]>: disassociated from <MAC 'WLAN-FINDHORN' [AC1]> (Reason: 2=PREV_AUTH_NOT_VALID)
[  599.139966] wlx<IF from MAC [IF2]>: authenticate with <MAC 'WLAN-FINDHORN' [AC1]>
[  599.144876] wlx<IF from MAC [IF2]>: send auth to <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  599.149040] wlx<IF from MAC [IF2]>: authenticated
[  599.150959] wlx<IF from MAC [IF2]>: associate with <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  599.156780] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'WLAN-FINDHORN' [AC1]> (capab=0x431 status=0 aid=6)
[  599.157387] usb 1-10: rtl8xxxu_bss_info_changed: HT supported
[  599.158023] wlx<IF from MAC [IF2]>: associated
[  602.169984] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[  673.069535] r8169 0000:01:00.0 enp1s0: link down
[  927.782636] wlx<IF from MAC [IF2]>: deauthenticating from <MAC 'WLAN-FINDHORN' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  928.632989] wlx<IF from MAC [IF2]>: authenticate with <MAC 'WLAN-FINDHORN' [AC1]>
[  928.643199] wlx<IF from MAC [IF2]>: send auth to <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  928.646594] wlx<IF from MAC [IF2]>: authenticated
[  928.648103] wlx<IF from MAC [IF2]>: associate with <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[  928.653538] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'WLAN-FINDHORN' [AC1]> (capab=0x431 status=0 aid=6)
[  928.654149] usb 1-10: rtl8xxxu_bss_info_changed: HT supported
[  928.654749] wlx<IF from MAC [IF2]>: associated
[ 1047.224106] r8169 0000:01:00.0 enp1s0: link up
[ 1539.239795] wlx<IF from MAC [IF2]>: authenticate with <MAC 'WLAN-FINDHORN' [AC1]>
[ 1539.248242] wlx<IF from MAC [IF2]>: send auth to <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[ 1539.251135] wlx<IF from MAC [IF2]>: authenticated
[ 1539.254816] wlx<IF from MAC [IF2]>: associate with <MAC 'WLAN-FINDHORN' [AC1]> (try 1/3)
[ 1539.261435] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'WLAN-FINDHORN' [AC1]> (capab=0x431 status=0 aid=3)
[ 1539.262061] usb 1-10: rtl8xxxu_bss_info_changed: HT supported
[ 1539.262664] wlx<IF from MAC [IF2]>: associated

########## wireless info END ############

```

---

### Post by chili555 on 2018-09-09
I am very surprised that your wireless seems to have an IPv6 address but not IPv4. I also note that the ethernet is connected and has proper appearing addresses. Usually, Network Manager will default to ethernet as it is generally more secure and faster. Please detach the ethernet, reboot and let us see a new wireless_info.

---

### Post by jonny62 on 2018-09-10
system rebooted with detach ethernet/lan
connected via wlan to router; connect to "some" internet web-pages: e.g. wikipedia can be found; ubuntuforums can't be found...??
no ip4 but ip6 address

```



########## wireless info START ##########

Report from: 10 Sep 2018 08:28 CEST +0200

Booted last: 10 Sep 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 18.3 Sylvia
Release:    18.3
Codename:    sylvia

##### kernel ############################

Linux 4.15.0-33-generic #36~16.04.1-Ubuntu SMP Wed Aug 15 17:21:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7a70]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04a9:1801 Canon, Inc. 
Bus 001 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 001 Device 002: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard G230
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 007: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

intel_wmi_thunderbolt    16384  0
rtl8xxxu              122880  0
mac80211              778240  1 rtl8xxxu
cfg80211              622592  1 mac80211
mxm_wmi                16384  0
wmi                    24576  2 intel_wmi_thunderbolt,mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback 

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34994 (34.9 KB)  TX bytes:34994 (34.9 KB)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          inet6 addr: 2a02:908:8a9:94e0:cac:7e50:406f:c296/64 Scope:Global
          inet6 addr: fe80::df43:2d2d:4fbf:83de/64 Scope:Link
          inet6 addr: 2a02:908:8a9:94e0:7eec:c166:53de:eb71/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1795 (1.7 KB)  TX bytes:7689 (7.6 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11  ESSID:"WLAN-FINDHORN"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WLAN-FINDHORN' [AC3]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       989     1  0 08:27 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 4.15.0-33-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WLAN-FINDHORN
GENERAL.CON-UUID:                       dfa40c43-4dfc-4620-8499-397e0178e05e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   dfa40c43-4dfc-4620-8499-397e0178e05e | WLAN-FINDHORN
IP6.ADDRESS[1]:                         2a02:908:8a9:94e0:cac:7e50:406f:c296/64
IP6.ADDRESS[2]:                         2a02:908:8a9:94e0:7eec:c166:53de:eb71/64
IP6.ADDRESS[3]:                         fe80::df43:2d2d:4fbf:83de/64
IP6.GATEWAY:                            fe80::464e:6dff:fe2b:92d8
IP6.ROUTE[1]:                           dst = 2a02:908:8a9:94e0::/59, nh = fe80::464e:6dff:fe2b:92d8, mt = 600
IP6.DNS[1]:                             fd00::464e:6dff:fe2b:92d8

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
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

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
WLAN-FINDHORN   <MAC 'WLAN-FINDHORN' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       yes     * 
devolo-e38      <MAC 'devolo-e38' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
FRITZ!Box 7490  <MAC 'FRITZ!Box 7490' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
QUINTUS2016     <MAC 'QUINTUS2016' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  14      &#9602;___  WPA1 WPA2  no        
devolo-b2c      <MAC 'devolo-b2c' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  10      &#9602;___  WPA2       no        
NSA-Spider      <MAC 'NSA-Spider' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  7       &#9602;___  WPA2       no        

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

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/WLAN-FINDHORN]] (600 root)
[connection] id=WLAN-FINDHORN | type=wifi | permissions=user:norbert:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=WLAN-FINDHORN
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (5725 - 5875 @ 80), (N/A, 13), (N/A)
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

wlx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'FRITZ!Box 7490' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7490"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000d913fb
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'devolo-e38' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"devolo-e38"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001d1e39359dbb
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'WLAN-FINDHORN' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"WLAN-FINDHORN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000945242591
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'devolo-b2c' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"devolo-b2c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000214d74419d2b
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'NSA-Spider' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"NSA-Spider"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000112e836f180
                    Extra: Last beacon: 244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'FRITZ!Box Fon WLAN 7390' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7390"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008ca9cd0d5
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (0) :
                        Authentication Suites (0) :
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (0) :
                        Authentication Suites (0) :
          Cell 07 - Address: <MAC 'QUINTUS2016' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"QUINTUS2016"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013a0322b173
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8723bu_bt.bin
firmware:       rtlwifi/rtl8723bu_nic.bin
firmware:       rtlwifi/rtl8192eu_nic.bin
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@gmail.com>
srcversion:     E7E78FAA920143C9B0CB35A
depends:        mac80211
retpoline:      Y
intree:         Y
name:           rtl8xxxu
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)
parm:           dma_aggregation:Enable DMA packet aggregation (bool)
parm:           dma_agg_timeout:Set DMA aggregation timeout (range 1-127) (int)
parm:           dma_agg_pages:Set DMA aggregation pages (range 1-127, 0 to disable) (int)

[mac80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     AFB624FD5B16A8AA59A9CF7
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_pages: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_aggregation: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_timeout: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

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

rtl8xxxu

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
blacklist rtl8192cu

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

mount -t ext4 /dev/sdb3 /media/norbert/DATA

mount --bind /media/norbert/DATA/Bilder  /home/norbert/Bilder
mount --bind /media/norbert/DATA/Videos  /home/norbert/Videos
mount --bind /media/norbert/DATA/Musik  /home/norbert/Musik

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    3.890259] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    3.950637] r8169 0000:01:00.0 enp1s0: link down
[    3.950722] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   28.210611] usb 1-10: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[   28.210632] usb 1-10: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   29.656194] rtl8xxxu 1-10:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[   29.684825] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[   31.424729] wlx<IF from MAC [IF2]>: authenticate with <MAC 'WLAN-FINDHORN' [AC3]>
[   31.430276] wlx<IF from MAC [IF2]>: send auth to <MAC 'WLAN-FINDHORN' [AC3]> (try 1/3)
[   31.433683] wlx<IF from MAC [IF2]>: authenticated
[   31.436337] wlx<IF from MAC [IF2]>: associate with <MAC 'WLAN-FINDHORN' [AC3]> (try 1/3)
[   31.443763] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'WLAN-FINDHORN' [AC3]> (capab=0x431 status=0 aid=1)
[   31.444312] usb 1-10: rtl8xxxu_bss_info_changed: HT supported
[   31.444916] wlx<IF from MAC [IF2]>: associated
[   35.446952] wlx<IF from MAC [IF2]>: disassociated from <MAC 'WLAN-FINDHORN' [AC3]> (Reason: 2=PREV_AUTH_NOT_VALID)
[   38.561815] wlx<IF from MAC [IF2]>: authenticate with <MAC 'WLAN-FINDHORN' [AC3]>
[   38.565967] wlx<IF from MAC [IF2]>: send auth to <MAC 'WLAN-FINDHORN' [AC3]> (try 1/3)
[   38.572730] wlx<IF from MAC [IF2]>: authenticated
[   38.580447] wlx<IF from MAC [IF2]>: associate with <MAC 'WLAN-FINDHORN' [AC3]> (try 1/3)
[   38.587929] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'WLAN-FINDHORN' [AC3]> (capab=0x431 status=0 aid=1)
[   38.588543] usb 1-10: rtl8xxxu_bss_info_changed: HT supported
[   38.589150] wlx<IF from MAC [IF2]>: associated
[   41.604528] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############




```

---

