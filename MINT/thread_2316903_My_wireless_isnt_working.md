---
title: "My wireless isnt working"
date: 2016-03-11
forum: MINT
---

### Post by vasecthomas on 2016-03-11
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)

4.2.0-30-generic #36~14.04.1-Ubuntu

---

### Post by Bucky Ball on 2016-03-11
*Thread moved to **Networking & Wireless**.*

Welcome. Not enough information. Please explain exactly what's happening, what you have found researching it and what you have tried from that. Provide links if relevant. 

Please run the wirelessinfo script and post the output here between code tags. You will find a link to the script in my signature at the bottom of this post and also a link for how to use code tags.

PS: Are you having other issues with that kernel? Is there any reason you are using that one instead of the default 3.13 for 14.04 LTS?

---

### Post by vasecthomas on 2016-03-11
```

########## wireless info START ##########

Report from: 11 Mar 2016 17:40 PST -0800

Booted last: 11 Mar 2016 16:26 PST -0800

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa

##### kernel ############################

Linux 4.2.0-30-generic #36~14.04.1-Ubuntu SMP Fri Feb 26 18:49:23 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8672]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: ASUSTeK Computer Inc. Device [1043:86e0]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 010: ID 05c6:6765 Qualcomm, Inc. 
Bus 001 Device 009: ID 0e8d:1887 MediaTek Inc. 
Bus 001 Device 008: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102/2.0 / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 006: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 004: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 003: ID 1a2c:0e24 China Resource Semico Co., Ltd 
Bus 001 Device 005: ID 0b05:1825 ASUSTek Computer, Inc. 
Bus 001 Device 002: ID 04e8:6863 Samsung Electronics Co., Ltd GT-I9500 [Galaxy S4] / GT-I9250 [Galaxy Nexus] (network tethering)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

eeepc_wmi              16384  0 
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
ath10k_pci             40960  0 
ath10k_core           278528  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              729088  1 ath10k_core
cfg80211              540672  3 ath,mac80211,ath10k_core
mxm_wmi                16384  0 
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:df200000-df220000 

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.172  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'usb0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90424 errors:8 dropped:0 overruns:0 frame:8
          TX packets:95217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80787109 (80.7 MB)  TX bytes:18151357 (18.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

usb0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1116     1  0 16:26 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: usb0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.172
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129

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

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

usb0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     5EB8A069F322875ED643860
depends:        ath10k_core
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6C:36:8A:BF:94:3C:D4:16:83:EB:2A:51:99:BF:B9:B4:01:ED:5A:B5
sig_hashalgo:   sha512
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     1374D8F96EF13D559461E8C
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6C:36:8A:BF:94:3C:D4:16:83:EB:2A:51:99:BF:B9:B4:01:ED:5A:B5
sig_hashalgo:   sha512
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)

[ath]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6C:36:8A:BF:94:3C:D4:16:83:EB:2A:51:99:BF:B9:B4:01:ED:5A:B5
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6C:36:8A:BF:94:3C:D4:16:83:EB:2A:51:99:BF:B9:B4:01:ED:5A:B5
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6C:36:8A:BF:94:3C:D4:16:83:EB:2A:51:99:BF:B9:B4:01:ED:5A:B5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
debug_mask: 0
skip_otp: N
uart_print: N

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x15b8 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x003e (ath10k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############

```


I've tried this

[http://ubuntuforums.org/showthread.php?t=2308578&highlight=qca6174](http://ubuntuforums.org/showthread.php?t=2308578&highlight=qca6174)

and this

```
    sudo apt-get install linux-generic-lts-wily
    wget https://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.156_all.deb
    sudo dpkg -i linux-firmware_1.156_all.deb
```

There is no wireless available in the network manager

---

### Post by Bucky Ball on 2016-03-11
*Thread moved to **MINT**.*

Mint is not supported in the main forum areas here. You may have more luck posting on the active Mint forum as well as here.

I can't see anything obvious in your output, but I am no expert (although it does appear that 'USB0' is being read as a wired connection in one instance). Hopefully someone else will drop by who is. Good luck.

---

### Post by vasecthomas on 2016-03-11
the USB is my tether

---

### Post by Bucky Ball on 2016-03-12
> **vasecthomas said:**
> the USB is my tether

So what are you trying to connect to wirelessly? The router? And what are you tethering? 

If you are trying to connect to a wireless router, I suggest you remove anything internet related except the wireless dongle you are trying to connect with. So get rid of any ethernet cable, USB tether, other wireless dongle, etc, then run the wirelessinfo script again with ONLY the wireless dongle plugged in and repost. Thanks.

---

### Post by vasecthomas on 2016-03-12
> **Bucky Ball said:**
> 

PS: Are you having other issues with that kernel? Is there any reason you are using that one instead of the default 3.13 for 14.04 LTS?

Using a different kernel was one of the many failed tips to try to get qca6174 to work. 

```

########## wireless info START ##########

Report from: 11 Mar 2016 23:57 PST -0800

Booted last: 11 Mar 2016 20:27 PST -0800

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa

##### kernel ############################

Linux 4.2.0-30-generic #36~14.04.1-Ubuntu SMP Fri Feb 26 18:49:23 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8672]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: ASUSTeK Computer Inc. Device [1043:86e0]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 05c6:6765 Qualcomm, Inc. 
Bus 001 Device 010: ID 0e8d:1887 MediaTek Inc. 
Bus 001 Device 009: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102/2.0 / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 008: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 006: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 004: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 003: ID 1a2c:0e24 China Resource Semico Co., Ltd 
Bus 001 Device 005: ID 0b05:1825 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             40960  0 
ath10k_core           282624  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              630784  1 ath10k_core
cfg80211              532480  3 ath,mac80211,ath10k_core
compat                 16384  3 cfg80211,mac80211,ath10k_pci
eeepc_wmi              16384  0 
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0 
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:df200000-df220000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       885     1  0 20:27 ?        00:00:13 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath10k_pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

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

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

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
          Channel 12 : 2.467 GHz
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
          Channel 144 : 5.72 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.2.0-30-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     2C3D5FA5797C89E8231F86B
depends:        ath10k_core,compat
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.2.0-30-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     2CEAB76811A0B05C303317D
depends:        mac80211,cfg80211,ath
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)

[ath]
filename:       /lib/modules/4.2.0-30-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       4.2.0-30-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-30-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
skip_otp: Y
uart_print: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
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

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y

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
# PCI device 0x8086:0x15b8 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x003e (ath10k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[12162.306344] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[12168.305503] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12173.748685] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12179.747607] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12185.190743] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12191.189801] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12196.632970] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12202.631999] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12208.075141] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12214.074221] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12219.525366] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12225.524558] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12230.967703] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[12236.966702] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12242.409767] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12248.408947] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12253.847942] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12259.847134] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12265.290275] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12271.289207] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12276.732346] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12282.731526] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12288.174540] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12294.173593] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12299.616774] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12305.615797] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12311.058936] ath10k_pci 0000:02:00.0: failed to enable adaptive qcs: -11
[12317.058011] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12322.501173] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12328.500265] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12333.943388] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[12339.942497] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12345.385534] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12351.384624] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12356.827771] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12362.826924] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12368.269936] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12374.268991] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12379.712166] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[12385.711192] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12391.158484] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[12397.157395] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12402.604557] ath10k_pci 0000:02:00.0: failed to enable ani by default: -11
[12408.603639] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12414.046735] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12420.045828] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12425.489070] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12431.488023] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12436.931157] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12442.930230] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12448.373473] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12454.372524] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12459.815532] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[12465.814618] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12471.257744] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12477.256794] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12482.699937] ath10k_pci 0000:02:00.0: failed to enable ani by default: -11
[12488.698996] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12494.142141] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[12500.141186] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12505.584464] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12511.583476] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12517.026567] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[12523.025683] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12528.468810] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12534.467922] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12539.910935] ath10k_pci 0000:02:00.0: failed to enable ani by default: -11
[12545.910126] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12551.353262] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[12557.352288] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12562.795459] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12568.794468] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12574.237602] ath10k_pci 0000:02:00.0: failed to enable adaptive qcs: -11
[12580.236644] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12585.679814] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[12591.678917] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12597.122041] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12603.121130] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12608.644144] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12614.643299] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12620.086386] ath10k_pci 0000:02:00.0: failed to enable ani by default: -11
[12626.085443] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12631.528587] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12637.527644] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12642.970789] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12648.969852] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12654.413016] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12660.412068] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12665.855180] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12671.854238] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12677.297435] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12683.296443] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[12688.739586] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[12694.738643] ath10k_pci 0000:02:00.0: could not suspend target (-11)

########## wireless info END ############


```

---

### Post by Bucky Ball on 2016-03-12
Check chili555's [post number 4 here]("http://ubuntuforums.org/showthread.php?t=2308578&p=13417605&viewfull=1#post13417605") (you will need to get online with an ethernet cable to perform those commands) and if still not working after reboot, continue with jeremy31's commands in post #6 on the same thread. Let us know how that goes.

I suggest you boot from the original kernel to perform these actions (which will be the highest 3.13.0-** kernel on the list).

---

### Post by Rob Sayer on 2016-03-12
> **Bucky Ball said:**
> Check chili555's [post number 4 here]("http://ubuntuforums.org/showthread.php?t=2308578&p=13417605&viewfull=1#post13417605") (you will need to get online with an ethernet cable to perform those commands) and if still not working after reboot, continue with jeremy31's commands in post #6 on the same thread. Let us know how that goes.

I suggest you boot from the original kernel to perform these actions (which will be the highest 3.13.0-** kernel on the list).

That'd be my suggestion too, allthough the kernel for Mint 17.3 is 3.19, not 3.13.  It's not hard to revert to the previous kernel in Mint.

---

### Post by Bucky Ball on 2016-03-12
> **Rob Sayer said:**
> That'd be my suggestion too, allthough the kernel for Mint 17.3 is 3.19, not 3.13.  It's not hard to revert to the previous kernel in Mint.

I see. Thanks for that. Guess that's why all Mint stuff goes here where people might have a clue about it. :)

---

### Post by vasecthomas on 2016-03-13
I followed all of those, no errors, still no wireless

---

### Post by jeremy31 on 2016-03-13
I would uninstall the backports as the 4.2 kernel does have support for that wireless
```
cd backports-20150903
sudo make uninstall
```

Reboot

Post ```
ls /lib/firmware/ath10k/QCA6174/hw3.0/
```

---

### Post by vasecthomas on 2016-03-13
```
ls /lib/firmware/ath10k/QCA6174/hw3.0/
board-2.bin     firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1
board.bin       notice.txt_WLAN.RM.2.0-00180-QCARMSWPZ-1
firmware-4.bin
```

---

### Post by Bucky Ball on 2016-03-13
@vasecthomas: Have added code tags to your last post. Please use them. See the link in my signature at bottom of this post for how. Thanks. :)

---

### Post by jeremy31 on 2016-03-14
We should try newer backports ```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz
tar -zxvf backports-4.4.2-1.tar.gz
cd backports-4.4.2-1
make defconfig-ath10k
make 
sudo make install
```

Reboot

---

