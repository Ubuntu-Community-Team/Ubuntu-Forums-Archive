---
title: "Network Manager not working."
date: 2017-01-27
forum: MINT
---

### Post by ny-paulie on 2017-01-27
I ran the wireless-info.sh script to generate a wireless-test.txt because I can no longer use the network app in my taskbar. I can connect via an ethernet cable and other devices have no problem. I tried the swapped-out hard drive in another similar machine and get the same problem. Here's the wireless-test.txt:


```
########## wireless info START ##########

Report from: 27 Jan 2017 14:33 EST -0500

Booted last: 27 Jan 2017 10:43 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa

##### kernel ############################

Linux 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

MATE

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
    Subsystem: Lenovo ThinkPad T61/R61 [17aa:20b9]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4230] (rev 61)
    Subsystem: Intel Corporation Lenovo ThinkPad T51 [8086:1110]
    Kernel driver in use: iwl4965

##### lsusb #############################

Bus 002 Device 002: ID 154b:0044 PNY 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04f3:02f4 Elan Microelectronics Corp. 2.4G Cordless Mouse
Bus 001 Device 005: ID 03f0:5511 Hewlett-Packard DeskJet F300 series
Bus 001 Device 004: ID 04b3:4487 IBM Corp. 
Bus 001 Device 003: ID 04b3:4486 IBM Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

##### lsmod #############################

iwl4965               114688  0 
iwlegacy              106496  1 iwl4965
mac80211              708608  2 iwl4965,iwlegacy
cfg80211              524288  3 iwl4965,iwlegacy,mac80211
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

iface wlan1 inet dhcp
wireless-key 0FB33F2571
wireless-essid 96PG2

auto wlan1

iface eth1 inet dhcp

auto eth1

##### ifconfig ##########################

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF1]>  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth1' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:136946935 (136.9 MB)  TX bytes:11340488 (11.3 MB)
          Interrupt:20 Memory:fe200000-fe220000 

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth1      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"96PG2"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
            Retry short limit:7   RTS thr:off   Fragment thr:off
            Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1

##### resolv.conf #######################

nameserver 192.168.0.1
nameserver 68.237.161.12
search domain_not_set.invalid

##### network managers ##################

Installed:

    NetworkManager

Running:

root      4731     1  0 11:07 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl4965
  State:             unmanaged
  Default:           no
  HW Address:        <MAC 'wlan1' [IF2]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unmanaged
  Default:           no
  HW Address:        <MAC 'eth1' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

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

no-auto-default=<MAC 'eth1' [IF1]>,<MAC address>,00:1E:37:90:7D:5D,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=NY Connection | type=802-11-wireless
[802-11-wireless] ssid=DG1670AC2-5G | mac-address=<MAC 'wlan1' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/PA Connection]] (600 root)
[connection] id=PA Connection | type=802-11-wireless
[802-11-wireless] ssid=IRNF6 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DG1670AC2]] (600 root)
[connection] id=DG1670AC2 | type=802-11-wireless
[802-11-wireless] ssid=DG1670AC2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DG1670AC2-5G 1]] (600 root)
[connection] id=DG1670AC2-5G 1 | type=802-11-wireless
[802-11-wireless] ssid=DG1670AC2-5G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DG1670AC2-5G]] (600 root)
[connection] id=DG1670AC2-5G | type=802-11-wireless
[802-11-wireless] ssid=DG1670AC2-5G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DG1670AC2 2]] (600 root)
[connection] id=DG1670AC2 2 | type=802-11-wireless
[802-11-wireless] ssid=DG1670AC2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DG1670AC2 1]] (600 root)
[connection] id=DG1670AC2 1 | type=802-11-wireless
[802-11-wireless] ssid=DG1670AC2 | mac-address=<MAC 'wlan1' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/96PG2]] (600 root)
[connection] id=96PG2 | type=802-11-wireless
[802-11-wireless] ssid=96PG2 | mac-address=<MAC 'wlan1' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DG1670AC2-5G 2]] (600 root)
[connection] id=DG1670AC2-5G 2 | type=802-11-wireless
[802-11-wireless] ssid=DG1670AC2-5G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth1      no frequency information.

lo        no frequency information.

wlan1     24 channels in total; available frequencies :
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

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Network is down

##### module infos ######################

[iwl4965]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
firmware:       iwlwifi-4965-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi 4965 driver for Linux
srcversion:     44589836474C711C0F43B03
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
  sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0 [disabled]) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     752C696EB47FC8BDCF872BB
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
  sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.19.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
  sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
 parm:           ieee80211_default_rc_algo"Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
  sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
  parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl4965]
11n_disable: 0
amsdu_size_8K: 0
fw_restart: 1
queues_num: 0
swcrypto: 0

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
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1049 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4230 (iwl4965)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x8086:0x1049 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x8086:0x4230 (iwl4965)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# PCI device 0x8086:0x4227 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
# PCI device 0x8086:0x1049 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x8086:0x4230 (iwl4965)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"
# PCI device 0x8086:0x1049 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

##### dmesg #############################

[   13.070945] iwl4965 0000:03:00.0 wlan1: renamed from wlan0
[   13.105939] systemd-udevd[422]: renamed network interface wlan0 to wlan1
[   14.185321] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   14.185438] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
[   14.185477] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1610.124202] e1000e: eth1 NIC Link is Down
[ 1752.656953] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 1752.657075] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
[ 5044.468225] e1000e: eth1 NIC Link is Down
[ 5053.929049] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 5053.929177] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
[ 5057.244227] e1000e: eth1 NIC Link is Down
[ 5058.981055] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 5058.981179] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
[ 5202.872207] e1000e: eth1 NIC Link is Down
[ 5211.385039] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 5211.385166] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
[ 5214.880218] e1000e: eth1 NIC Link is Down
[ 5216.601052] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 5216.601179] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO

########## wireless info END ############

```
I would appreciate anyone's help.

---

### Post by wildmanne39 on 2017-01-27
*Thread moved to **MINT for better support**.*

---

