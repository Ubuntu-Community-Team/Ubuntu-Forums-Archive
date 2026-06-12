---
title: "Driver with ndiswrapped, installed wrong"
date: 2017-06-02
forum: MINT
---

### Post by adelpozoman-f on 2017-06-02
Hello. Mint started getting very bad performance with the usb wifi dongle, what doesnt happens on windows, and I decided to giv ndiswrapped a try installing the windows drivers for my TL-WN722N Tp link. In fact, it didnt work, when connecting it stuck together and ask for password every 30 seconds. Now there is the problem When I wanted to go backward, uninstalled ndiswrapped drivers and reboot, linux mint didnt recognized the usb wifi, I have tried all that I have seen and have no clue what to do. 

In short: what is the fastest and more effective way to reset all native kernel drivers to its original state?. Thanks

---

### Post by howefield on 2017-06-02
Thread moved to the "*MINT*" forum.

---

### Post by jeremy31 on 2017-06-02
Linux Mint 18?  If you have actually removed ndiswrapper you should see nothing about ndiswrapper in results for ```
dkms status; dpkg -l | grep ndiswrapper
```

You may also see improvements by disabling wifi power management by doing ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

With the WN722N plugged in post results from terminal for ```
lsusb
```
There seems to be a second version of this device around

---

### Post by adelpozoman-f on 2017-06-03
dkms status; dpkg -l | grep ndiswrapper        Returned the following (I didnt uninstall ndiswrapper, I uninstalled ndiswrapper drivers with ndiswrapper -e (driver)):
fglrx-core, 15.201.2, 3.13.0-119-generic, x86_64: installed
fglrx-core, 15.201.2, 3.19.0-32-generic, amd64: installed
ndiswrapper, 1.59, 3.19.0-32-generic, x86_64: installed (WARNING! Diff between built and installed module!)
virtualbox-guest, 5.0.4, 3.19.0-32-generic, x86_64: installed (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!)
ii  mintwifi                                    2.0                                                 all          Collection of drivers for you to configure your wireless card through ndiswrapper without connecting to the Internet.
ii  ndiswrapper-common                          1.59-2                                              all          Common scripts required to use the utilities for ndiswrapper
ii  ndiswrapper-dkms                            1.59-2                                              all          Source for the ndiswrapper Linux kernel module (DKMS)
ii  ndiswrapper-utils-1.9                       1.59-2                                              amd64        Userspace utilities for the ndiswrapper Linux kernel module


Then lsusb returns:
fglrx-core, 15.201.2, 3.13.0-119-generic, x86_64: installed
fglrx-core, 15.201.2, 3.19.0-32-generic, amd64: installed
ndiswrapper, 1.59, 3.19.0-32-generic, x86_64: installed (WARNING! Diff between built and installed module!)
virtualbox-guest, 5.0.4, 3.19.0-32-generic, x86_64: installed (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!)
ii  mintwifi                                    2.0                                                 all          Collection of drivers for you to configure your wireless card through ndiswrapper without connecting to the Internet.
ii  ndiswrapper-common                          1.59-2                                              all          Common scripts required to use the utilities for ndiswrapper
ii  ndiswrapper-dkms                            1.59-2                                              all          Source for the ndiswrapper Linux kernel module (DKMS)
ii  ndiswrapper-utils-1.9                       1.59-2                                              amd64        Userspace utilities for the ndiswrapper Linux kernel module

Looks like device 006, any thoughts? thanks

---

### Post by jeremy31 on 2017-06-03
I don't see lsusb results

---

### Post by adelpozoman-f on 2017-06-03
> **jeremy31 said:**
> I don't see lsusb results

oh sorry:[EDITED, THAT WAS OTHER]:
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 005 Device 002: ID 054c:0155 Sony Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 002: ID 14cd:168a Super Top 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by jeremy31 on 2017-06-03
Post results for ```
modprobe -c | grep 9271
```

---

### Post by adelpozoman-f on 2017-06-03
modprobe -c \ grep 9271 returned this:

alias usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*in* ath9k_htc


is that significant?

---

### Post by jeremy31 on 2017-06-03
Use ```
ndiswrapper -l
```
And see if it is still using a windows driver

---

### Post by adelpozoman-f on 2017-06-03
it doesnt return anything.

---

### Post by jeremy31 on 2017-06-03
See the wireless script link in my signature and post results.
Since you are using Mint, don't run the sudo apt-get commands

---

### Post by adelpozoman-f on 2017-06-04
> **jeremy31 said:**
> See the wireless script link in my signature and post results.
Since you are using Mint, don't run the sudo apt-get commands

There you have:

```



########## wireless info START ##########

Report from: 04 Jun 2017 10:47 CEST +0200

Booted last: 04 Jun 2017 10:41 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa

##### kernel ############################

Linux 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Cinnamon

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 005 Device 002: ID 054c:0155 Sony Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 002: ID 14cd:168a Super Top 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

rt73usb                32768  0 
rt2x00usb              24576  1 rt73usb
rt2x00lib              57344  2 rt73usb,rt2x00usb
mac80211              708608  2 rt2x00lib,rt2x00usb
cfg80211              524288  2 mac80211,rt2x00lib
crc_itu_t              16384  1 rt73usb

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

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:168112 (168.1 KB)  TX bytes:168112 (168.1 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       954     1  0 10:41 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

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

[[/etc/NetworkManager/system-connections/Auto Orange-BEF6]] (600 root)
[connection] id=Auto Orange-BEF6 | type=802-11-wireless
[802-11-wireless] ssid=Orange-BEF6 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto Orange-919A]] (600 root)
[connection] id=Auto Orange-919A | type=802-11-wireless
[802-11-wireless] ssid=Orange-919A | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto Orange-919A-0252f7e1-ba1a-4566-b336-2e0d70204d39]] (600 root)
[connection] id=Auto Orange-919A | type=802-11-wireless
[802-11-wireless] ssid=Orange-919A | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto G4_3520]] (600 root)
[connection] id=Auto G4_3520 | type=802-11-wireless
[802-11-wireless] ssid=G4_3520 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rt73usb]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     BCF882E0CB338C7C3C172CF
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B51D09F4F13F9196B61EBE4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
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

[rt73usb]
nohwcrypt: N

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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist ndiswrapper

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
alias usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[  182.071686] ieee80211 phy1: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset (repeated 2 times)
[  258.007924] wlan1: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  303.311099] ieee80211 phy2: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[  303.326921] rt73usb 1-5:1.0 wlan1: renamed from wlan0
[  303.344941] systemd-udevd[5639]: renamed network interface wlan0 to wlan1
[  303.346062] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[  303.346092] ieee80211 phy2: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[  303.425566] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  305.899449] wlan1: authenticate with <MAC address>
[  305.960059] wlan1: send auth to <MAC address> (try 1/3)
[  305.964214] wlan1: authenticated
[  305.966222] wlan1: associate with <MAC address> (try 1/3)
[  305.969141] wlan1: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[  305.979893] wlan1: associated
[  305.979970] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  305.990161] wlan1: deauthenticating from <MAC address> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  306.049522] wlan1: authenticate with <MAC address>
[  306.081554] wlan1: send auth to <MAC address> (try 1/3)
[  306.083196] wlan1: authenticated
[  306.086277] wlan1: associate with <MAC address> (try 1/3)
[  306.089138] wlan1: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[  306.099663] wlan1: associated
[  402.356386] wlan1: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############


```


PD: nice script

---

### Post by jeremy31 on 2017-06-04
For some reason a config file for ndiswrapper wasn't removed
```
sudo rm /etc/modprobe.d/ndiswrapper.conf
```
```
sudo depmod -a
```
Reboot

---

### Post by adelpozoman-f on 2017-06-04
Ok, now it works pretty well (not exactly well, but just like before using ndis), just took a long time to connect to the network. Thanks!!!!!!!!!

---

### Post by jeremy31 on 2017-06-04
See chili555's post [here](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
See if some tweaks will improve it

---

