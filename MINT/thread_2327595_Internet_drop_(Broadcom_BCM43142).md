---
title: "Internet drop (Broadcom BCM43142)"
date: 2016-06-12
forum: MINT
---

### Post by jevisan on 2016-06-12
Greetings, i've been struggling for a while now with a low wifi signal whenever i step away from my router, a distance from which any other devices would connect without a problem. The signal just drops and makes internet completely unusable.

My computer has a Broadcom BCM43142 as a wireless chip.

It remains to say that i've already tried several solutions without any improvement. If you could provide a solution it would be greatly appreciated.

The wireless script run as follows:

```



########## wireless info START ##########


Report from: 12 Jun 2016 13:49 CDT -0500


Booted last: 12 Jun 2016 13:06 CDT -0500


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	LinuxMint
Description:	Linux Mint 17.3 Rosa
Release:	17.3
Codename:	rosa


##### kernel ############################


Linux 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lenovo Device [17aa:0621]
	Kernel driver in use: wl


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:3812]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 004: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 004 Device 003: ID 0c45:6513 Microdia 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


r8712u                184320  0 
b43                   421888  0 
bcma                   53248  1 b43
mac80211              708608  1 b43
ssb                    65536  1 b43
wl                   6369280  0 
ndiswrapper           286720  0 
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
cfg80211              524288  3 wl,b43,mac80211


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37139 errors:0 dropped:0 overruns:0 frame:2045
          TX packets:35607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30297416 (30.2 MB)  TX bytes:8711856 (8.7 MB)
          Interrupt:40 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"ARRIS-AB02"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'ARRIS-AB02' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1223     1  0 13:06 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [ARRIS-AB02 automática] --------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF2]>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    invitados Neos Control: Infra, <MAC 'xxxxx' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Red Apple Neos Control: Infra, <MAC 'xxxxx' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    *ARRIS-AB02:     Infra, <MAC 'xxxxx' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 85 WPA2
    MOTOROLA-26AC0:  Infra, <MAC 'MOTOROLA-26AC0' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA


  IPv4 Settings:
    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             10.2.9.34
    DNS:             10.3.9.34


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/WUAMC automática]] (600 root)
[connection] id=xxxxx automática | type=802-11-wireless
[802-11-wireless] ssid=xxxxx | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xxxxx automática]] (600 root)
[connection] id=xxxxx automática | type=802-11-wireless
[802-11-wireless] ssid=xxxx | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xxxxx]] (600 root)
[connection] id=xxxxx | type=802-11-wireless
[802-11-wireless] ssid=xxxxx | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/xxxxx automática-23cf61bb-b6b3-48be-8dd3-6c8cd7070dc6]] (600 root)
[connection] id=xxxxx automática | type=802-11-wireless
[802-11-wireless] ssid=xxxxx | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xxxxx]] (600 root)
[connection] id=xxxxx | type=802-11-wireless
[802-11-wireless] ssid=xxxxxx | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Mexico_City (based on set time zone)


country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     32 channels in total; available frequencies :
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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ARRIS-AB02' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"ARRIS-AB02"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'xxxxx' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'xxxxxxx' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:"xxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[r8712u]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     71E662178E6926824122B39
depends:        
staging:        Y
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)


[b43]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     11BDA0A580599B083FE4F2B
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)


[bcma]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512


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
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[ssb]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     551AE4C23939F7FBED9DA61
depends:        
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512


[wl]
filename:       /lib/modules/3.19.0-32-generic/updates/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[ndiswrapper]
filename:       /lib/modules/3.19.0-32-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


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


[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0


[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc
wl
b43
ndiswrapper


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000014E4d00004365sv00002230sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004365sv00002232sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004365sv000022D3sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004365sv000022D4sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004365sv*sd*bc*sc*i* ndiswrapper
alias usb:v043Ep3001d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050DpD321d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0A5CpBD13d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v13B1p0039d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v13B1p003Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (775 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


##### dmesg #############################


[   17.273181] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   24.407894] r8169 0000:02:00.0 eth0: link down
[   24.407977] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  674.633535] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[  674.634654] r8712u: Staging version
[  674.634683] r8712u: register rtl8712_netdev_ops to netdev_ops
[  674.634690] usb 3-1.4: r8712u: USB_SPEED_HIGH with 4 endpoints
[  674.635206] usb 3-1.4: r8712u: Boot from EFUSE: Autoload OK
[  675.285683] usb 3-1.4: r8712u: CustomerID = 0x0000
[  675.285695] usb 3-1.4: r8712u: MAC Address from efuse = <MAC address>
[  675.285702] usb 3-1.4: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  675.390615] r8712u 3-1.4:1.0 wlan2: renamed from wlan1
[  675.404588] systemd-udevd[3406]: renamed network interface wlan1 to wlan2
[  676.120739] r8712u 3-1.4:1.0 wlan2: 1 RCR=0x153f00e
[  676.121501] r8712u 3-1.4:1.0 wlan2: 2 RCR=0x553f00e
[  676.228546] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready (repeated 2 times)
[ 1725.665046] ERROR @wl_dev_intvar_get : error (-1) (repeated 2 times)


########## wireless info END ############



```

---

### Post by Hadaka on 2016-06-12
Hi, looks like you have been very "busy". The following MUST
be done from a working wired connection. Please Copy and paste
one line at a time.*Ignore any an all errors just do the next line
ALL lines of this code need to be entered,
```
sudo iw reg set MX
sudo sed -i 's/^REG.*=$/&MX/' /etc/default/crda
```
then do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get install bcmwl-kernel-source
```
then do.
```
sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
```
Then do.
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
sudo modprobe wl
```
disconnect wired connection...boot...test wireless
thanks.

---

### Post by jevisan on 2016-06-12
As I understand, this just reinstalled the driver and purged conflicting packages, right?

Well, after several pings it went from losing 50 - 60% of packages to only 20% of packet loss and while the pages still take a while to load, at least they load completely instead of just some of the content.

So it's not optimal but it's a real improvement.

Is there anything else i can do, should i run the wireless script again to show the results?

In any case, thank you very much

---

### Post by Hadaka on 2016-06-12
Yes, please run a fresh wireless report..
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
thanks.

---

### Post by jevisan on 2016-06-12
with pleasure

here it is:
```



########## wireless info START ##########


Report from: 12 Jun 2016 19:15 CDT -0500


Booted last: 12 Jun 2016 17:07 CDT -0500


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	LinuxMint
Description:	Linux Mint 17.3 Rosa
Release:	17.3
Codename:	rosa


##### kernel ############################


Linux 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lenovo Device [17aa:0621]
	Kernel driver in use: wl


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:3812]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 004: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 004 Device 003: ID 0c45:6513 Microdia 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ndiswrapper           286720  0 
b43                   421888  0 
bcma                   53248  1 b43
mac80211              708608  1 b43
ssb                    65536  1 b43
wl                   6369280  0 
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
cfg80211              524288  3 wl,b43,mac80211


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:10.0.1.17  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:260182 errors:0 dropped:0 overruns:0 frame:34409
          TX packets:163547 errors:300 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:329226202 (329.2 MB)  TX bytes:20766263 (20.7 MB)
          Interrupt:43 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"xxxxx"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'xxxxxxx' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.1.1        0.0.0.0         UG    0      0        0 wlan0
10.0.1.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1031     1  0 17:07 ?        00:00:01 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [xxxxxxx] --------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF2]>


  Capabilities:
    Speed:           58 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    xxxxx:        Infra, <MAC 'OSO TITO' [AC4]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    *xxxxx: Infra, <MAC 'xxxxx' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    xxxxxx: Infra, <MAC 'xxxxx' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    xxxxx:      Infra, <MAC 'xxxxxx' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 65 WPA2
    INFINITUMDCC1:   Infra, <MAC 'INFINITUMDCC1' [AC3]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    jessy22:         Infra, <MAC 'jessy22' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WEP
    INFINITUMC0E5:   Infra, <MAC 'INFINITUMC0E5' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    ARRIS-98B2:      Infra, <MAC 'ARRIS-98B2' [AN8]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 22 WPA2
    MOTOROLA-26AC0:  Infra, <MAC 'MOTOROLA-26AC0' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA


  IPv4 Settings:
    Address:         10.0.1.17
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.1.1


    DNS:             10.0.1.1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/WUAMC automática]] (600 root)
[connection] id=WUAMC automática | type=802-11-wireless
[802-11-wireless] ssid=WUAMC | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xxxxx automática]] (600 root)
[connection] id=xxxxxx automática | type=802-11-wireless
[802-11-wireless] ssid=xxxxxx | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xxxxxx]] (600 root)
[connection] id=xxxxxx | type=802-11-wireless
[802-11-wireless] ssid=xxxxxx | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/xxxxxx automática-23cf61bb-b6b3-48be-8dd3-6c8cd7070dc6]] (600 root)
[connection] id=xxxxxx automática | type=802-11-wireless
[802-11-wireless] ssid=xxxxxx | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xxxxx automática]] (600 root)
[connection] id=xxxxx automática | type=802-11-wireless
[802-11-wireless] ssid=xxxxxxx | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Mexico_City (based on set time zone)


country MX:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 23), DFS
	(5735 - 5835 @ 40), (3, 30)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     27 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'xxxxxxx' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"xxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'xxxxx' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'INFINITUMDCC1' [AC3]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"INFINITUMDCC1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'xxxxx' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"OSO TITO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'xxxxxx' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"ARRIS-AB02"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ndiswrapper]
filename:       /lib/modules/3.19.0-32-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


[b43]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     11BDA0A580599B083FE4F2B
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)


[bcma]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512


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
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[ssb]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     551AE4C23939F7FBED9DA61
depends:        
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512


[wl]
filename:       /lib/modules/3.19.0-32-generic/updates/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


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


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2


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
wl
b43
ndiswrapper


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (775 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   16.866846] wl: module license 'MIXED/Proprietary' taints kernel. (repeated 2 times)
[   16.876895] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   17.024338] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   17.090865] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   23.536414] r8169 0000:02:00.0 eth0: link down
[   23.536522] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7705.743387] ERROR @wl_dev_intvar_get : error (-1)


########## wireless info END ############



```

---

### Post by Hadaka on 2016-06-12
Ok, the drivers got reloaded so we need to do the same commands again
From a working wired connection Please copy and paste..one line at a time..all lines
```
sudo sed -i '/^b43/ d' /etc/modules
sudo sed -i '/^ndiswrapper/ d' /etc/modules
```
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get install bcmwl-kernel-source
```
```
sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
sudo modprobe wl
```
remove wired connection,,boot,,,test wireless

then access your router configuration and remove the TKIP setting change it to WPA2 AES
next click your network manager,,the wifi icon..and then Edit connections
configure your connections like the attached set the IPv6 to Ignore.
[ATTACH=CONFIG]269559[/ATTACH]

---

### Post by howefield on 2016-06-13
Moved to the "*MINT*" forum.

---

### Post by jevisan on 2016-06-13
Ok, i reinstalled as requested and changed the connection to wpa2.

the wireless script output is:

```



########## wireless info START ##########


Report from: 13 Jun 2016 09:32 CDT -0500


Booted last: 13 Jun 2016 09:24 CDT -0500


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	LinuxMint
Description:	Linux Mint 17.3 Rosa
Release:	17.3
Codename:	rosa


##### kernel ############################


Linux 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lenovo Device [17aa:0621]
	Kernel driver in use: wl


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:3812]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 004: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 004 Device 003: ID 0c45:6513 Microdia 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


wl                   6369280  0 
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
cfg80211              524288  1 wl


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:10.0.1.17  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1144 errors:0 dropped:0 overruns:0 frame:484
          TX packets:1604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:619359 (619.3 KB)  TX bytes:273750 (273.7 KB)
          Interrupt:43 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"xxxxx"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'xxxxx' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.1.1        0.0.0.0         UG    0      0        0 wlan0
10.0.1.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1082     1  0 09:24 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [xxxxx] --------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF2]>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    xxxxx: Infra, <MAC 'xxxxx' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    xxxxx:      Infra, <MAC 'xxxxx' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    xxxxx:        Infra, <MAC 'xxxxx' [AC3]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    *xxxxx: Infra, <MAC 'xxxxx' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA2


  IPv4 Settings:
    Address:         10.0.1.17
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.1.1


    DNS:             10.0.1.1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/WUAMC automática]] (600 root)
[connection] id=WUAMC automática | type=802-11-wireless
[802-11-wireless] ssid=WUAMC | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xxxxx automática]] (600 root)
[connection] id=xxxxx automática | type=802-11-wireless
[802-11-wireless] ssid=xxxxx | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xxxxx]] (600 root)
[connection] id=xxxxx | type=802-11-wireless
[802-11-wireless] ssid=xxxxx | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/xxxxx automática-23cf61bb-b6b3-48be-8dd3-6c8cd7070dc6]] (600 root)
[connection] id=xxxxx automática | type=802-11-wireless
[802-11-wireless] ssid=xxxxx | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xxxxx automática]] (600 root)
[connection] id=xxxxx automática | type=802-11-wireless
[802-11-wireless] ssid=xxxxx | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Mexico_City (based on set time zone)


country MX:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 23), DFS
	(5735 - 5835 @ 40), (3, 30)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     27 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'xxxxx' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"xxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'xxxxx' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"xxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'xxxxx' [AC3]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"xxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'xxxxx' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"xxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[wl]
filename:       /lib/modules/3.19.0-32-generic/updates/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


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


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc
wl


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (775 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   16.973351] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.983801] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   17.132566] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   23.421050] r8169 0000:02:00.0 eth0: link down
[   23.421136] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  502.929221] ERROR @wl_dev_intvar_get : error (-1)


########## wireless info END ############



```

---

### Post by lewj85 on 2016-10-19
I'm having similar problems. I followed the steps in this thread and it didn't make a noticeable improvement. Has anyone else with a BCM43142 figured out a way to prevent their internet from dropping randomly?

---

