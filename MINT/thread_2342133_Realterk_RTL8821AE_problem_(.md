---
title: "Realterk RTL8821AE problem :("
date: 2016-11-04
forum: MINT
---

### Post by milo-donati on 2016-11-04
Hi all, i disabled my wi-fi card from menu and now the menu item is disabled.

This is output o wireless-info script
```



########## wireless info START ##########


Report from: 04 Nov 2016 11:14 CET +0100


Booted last: 04 Nov 2016 10:45 CET +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa


##### kernel ############################


Linux 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


MATE


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:205f]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: XAVi Technologies Corp. Device [1b9a:2482]
    Kernel driver in use: rtl8821ae


##### lsusb #############################


Bus 003 Device 003: ID b49a:04f2  
Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rtl8821ae             323584  0 
btcoexist              57344  1 rtl8821ae
rtl_pci                40960  1 rtl8821ae
rtlwifi               106496  2 rtl_pci,rtl8821ae
mac80211              573440  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              499712  2 mac80211,rtlwifi
compat                 16384  5 cfg80211,mac80211,btcoexist,rtlwifi,rtl8821ae
mxm_wmi                16384  1 nouveau
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
video                  20480  3 i915_bpo,nouveau,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:10.224.129.81  Bcast:10.224.129.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13013686 (13.0 MB)  TX bytes:2521696 (2.5 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.224.129.201  0.0.0.0         UG    0      0        0 eth0
10.224.129.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1300     1  0 10:45 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8821ae
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


- Device: eth0  [Connessione via cavo 1] ---------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         10.224.129.81
    Prefix:          24 (255.255.255.0)
    Gateway:         10.224.129.201


    DNS:             10.224.129.12
    DNS:             10.233.194.3
    DNS:             10.233.194.4


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Telecom-61733093]] (600 root)
[connection] id=Telecom-61733093 | type=802-11-wireless
[802-11-wireless] ssid=Telecom-61733093 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/InfostradaWiFi-0C2EFE]] (600 root)
[connection] id=InfostradaWiFi-0C2EFE | type=802-11-wireless
[802-11-wireless] ssid=InfostradaWiFi-0C2EFE | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CarrefourFree]] (600 root)
[connection] id=CarrefourFree | type=802-11-wireless
[802-11-wireless] ssid=CarrefourFree | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Telecom-22861893]] (600 root)
[connection] id=Telecom-22861893 | type=802-11-wireless
[802-11-wireless] ssid=Telecom-22861893 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FASTWEB-1-17AB41]] (600 root)
[connection] id=FASTWEB-1-17AB41 | type=802-11-wireless
[802-11-wireless] ssid=FASTWEB-1-17AB41 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/3.19.0-32-generic/updates/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     E7F30880CD784BEF26E6721
depends:        rtlwifi,rtl_pci,compat,btcoexist,mac80211
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
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


[rtl_pci]
filename:       /lib/modules/3.19.0-32-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     7C41A4007A6094567567091
depends:        mac80211,rtlwifi
vermagic:       3.19.0-32-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/3.19.0-32-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     44A5F49216740D2B9E16476
depends:        mac80211,compat,cfg80211
vermagic:       3.19.0-32-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-32-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
srcversion:     2E526B72B7E114629FB8EA1
depends:        cfg80211,compat
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-32-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     07F008E2B6279F6399E5939
depends:        compat
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: Y
swenc: N
swlps: N


[mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/asus_nb_wmi.conf]
options asus_nb_wmi wapf=1


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  177.348390] r8169 0000:02:00.0 eth0: link down
[  191.054020] r8169 0000:02:00.0 eth0: link up


########## wireless info END ############




```

I see wifi is soft-blocked but functionKey + f2 (wireless) not enabled it.


This is the output of "modinfo rtl8821ae"

```

filename:       /lib/modules/3.19.0-32-generic/updates/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     E7F30880CD784BEF26E6721
alias:          pci:v000010ECd00008821sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008812sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,compat,btcoexist,mac80211
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
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

```

Can you help me please :( ????
Thank you

---

### Post by howefield on 2016-11-04
Thread moved to the "*MINT*" sub forum.

---

