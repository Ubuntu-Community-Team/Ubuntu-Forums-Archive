---
title: "RTL8723be problems on HP250G2"
date: 2016-06-12
forum: MINT
---

### Post by jojo11 on 2016-06-12
Hi , have reading all interesting threads about this problem. More then two days try to solve it with different combination for this driver (rtlwifi_new by LW Finger) but no solution yet. Can see full strength of signal, connect to ap but not to internet- It is horrible. Please can somebody help me, want not to change w.... THANKS in advance!!!!
Here my wireless info:

```
##########  START ##########

Report from: 12 Jun 2016 15:03 CEST +0200

Booted last: 12 Jun 2016 14:48 CEST +0200

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa

##### kernel ############################

Linux 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80cb]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 05c8:022a Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
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

hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtl8723be             143360  0 
btcoexist             413696  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               135168  3 btcoexist,rtl_pci,rtl8723be
mac80211              708608  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.178.42  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1820387 (1.8 MB)  TX bytes:621965 (621.9 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.178.40  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68084 (68.0 KB)  TX bytes:21528 (21.5 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BXc34u3"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'BXc34u3' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr
          Power Managementff
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 eth0
192.168.178.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.178.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search fritz.box

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1161     1  0 14:48 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
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
    Address:         192.168.178.42
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.178.1

    DNS:             192.168.178.1

- Device: wlan0  [BXc3u3] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    10418b:          Infra, <MAC '10418b' [AC2]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    *BXc34u3:        Infra, <MAC 'BXc34u3' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    BXc34u3:         Infra, <MAC 'BXc34u3' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2

  IPv4 Settings:
    Address:         192.168.178.40
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.178.1

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

[[/etc/NetworkManager/system-connections/Automatisch BXc34u4]] (600 root)
[connection] id=Automatisch BXc34u4 | type=802-11-wireless
[802-11-wireless] ssid=BXc34u4 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BXc34u3]] (600 root)
[connection] id=BXc34u3 | type=802-11-wireless
[802-11-wireless] ssid=BXy34u3 | bssid=<MAC 'BXc343' [AC1]> | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Automatisch 10418b]] (600 root)
[connection] id=Automatisch 104xb | type=802-11-wireless
[802-11-wireless] ssid=104x8b | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'BXc4u3' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption keyn
                    ESSID:"BXc4u3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000061fa5c20c
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '10418b' [AC2]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption keyn
                    ESSID:"10418b"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000033e57a5335
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     2DA37D00E0E770F2130B511
depends:        rtl_pci,rtlwifi,btcoexist,mac80211
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl_pci]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     19F641F4D415757EC664242
depends:        mac80211,rtlwifi
vermagic:       3.19.0-32-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3543BCA40961E4EED7C3D89
depends:        mac80211,cfg80211
vermagic:       3.19.0-32-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E48:99:09:26:11:7AA:3B:EB:41:9C
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algoefault rate control algorithm for mac80211 to use (charp)

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
sig_key:        0C:8B:EF:E0:C1:E2:89:E48:99:09:26:11:7AA:3BF:EB:41:9C
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
ant_sel: 2
debug: 1
disable_watchdog: N
fwlps: N
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

[/etc/modprobe.d/rtl8723b3.conf]
options rtl8723be msi=1

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N
options rtl8723be ant_sel=2

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   15.562152] rtlwifi: module verification failed: signature and/or  required key missing - tainting kernel
[   15.693376] Using firmware rtlwifi/rtl8723befw.bin
[   15.713173] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.713683] rtlwifi: wireless switch is on
[   19.973544] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.232143] r8169 0000:03:00.0 eth0: link down
[   20.232235] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.564305] wlan0: authenticate with <MAC 'BXc34u3' [AC1]>
[   21.575890] wlan0: direct probe to <MAC 'BXc34u3' [AC1]> (try 1/3)
[   21.778993] wlan0: send auth to <MAC 'BXc34u3' [AC1]> (try 2/3)
[   21.784046] wlan0: authenticated
[   21.787002] wlan0: associate with <MAC 'BXc34u3' [AC1]> (try 1/3)
[   21.794194] wlan0: RX AssocResp from <MAC 'BXc34u3' [AC1]> (capab=0x431 status=0 aid=1)
[   21.798350] wlan0: associated
[   21.798374] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  144.401703] r8169 0000:03:00.0 eth0: link up
[  144.401724] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############
```

---

### Post by jeremy31 on 2016-06-12
Can you change wifi router encryption to WPA2-AES, WPA2-PSK, or WPA2 only?  Linux usually struggles with TKIP encryption

---

### Post by jojo11 on 2016-06-12
anging toHello Jeremy31,
first thank for your hint !! But after changing to all after a another and reboot, same problem, can get to ap but no internet connection.
I' writing this with LAN connection. Thanks for more help!
jojo11

---

### Post by jeremy31 on 2016-06-12
Can you ping the ap using wifi and try ```
ping -c3 8.8.8.8
```
Also try ```
echo "options rtl8723be ips=N" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
```

Part of the script results shows
```
*BXc34u3:        Infra, <MAC 'BXc34u3' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    BXc34u3:         Infra, <MAC 'BXc34u3' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
```
Which is a bit strange for most people to have the same name for 2 ap's on the same channel

---

### Post by jojo11 on 2016-06-12
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=59 time=28.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=59 time=27.8 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=59 time=28.3 ms
and
echo "options rtl8723be ips=N" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
done....
with
* BXc34u3:        Infra, <MAC 'BXc34u3' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    BXc34u3:         Infra, <MAC 'BXc34u3' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
I don't know what you mean, because  the same config with ubunu 12.04 and 8 other Pcs are in the home wlan.
These are the first deepest trouble I have with this notebook....
Do not know how to handle this.
Thanky for your patience...
jojo11

---

### Post by jeremy31 on 2016-06-12
You can ping to the outside world, a good sign.  Change the Network Manager IPv6 settings for wireless to ignore and add 8.8.8.8 as a DNS server.  Reboot

---

### Post by jojo11 on 2016-06-13
Hi, thanks. Can only make settings without IPv6. If I want to setup DNS 8.8.8.8. "Apply " is greyed out.
There are only the possibility manual, automatic, automatic DHCP only,link local only. "Ignore" is no option....:(

Hi jeremy31, THANK YOU!!!
After creating a new wirless connection without IPv6 an no DNS,  I get in .
So my solution fot hp250g2 is for rtl8723.conf:
```
options rtl8723be fwlps=N
options rtl8723be ant_sel=2
options rtl8723be ips=N
2. Ignore IPv6
```

If necessary  built a new wireless connection, such a I have done...

Thank you once more jeremy31.

 
 One problem still exist, have sometimes drop outs and no bluetooth device
 was founf on both sides….
 jojo11

---

### Post by jojo11 on 2016-06-23
OK for reading and get tips from the forum  I return to here, to post that my problem is solved. This solution I want to describe for others user, which have also trouble to set up the driver in LM or Virtualbox for W...7. My notebook is not a HP250 G2 but a G4, but his does not matter.... I want to describe a solution with LM17.3 and W7 in Virtualbox. Fist part for LM17. is above: o my solution fot hp250g2 is for rtl8723.conf: options rtl8723be fwlps=N options rtl8723be ant_sel=2 options rtl8723be ips=N 2. Ignore IPv6  second part for a W7 in virrtualbox 1. install the drivers from HP homepage (Lenovos for rtl8723be  work also) 2. install oracle guest additions 3. for the virtual machine in change mode: got to network and set it up if you want LAN: change to ath0 if you wan WLAN: change it to wlan0 for every VM! the Network manager jump the to network 2 and the LAN Symbol stays in iconbar, the icon did not change to the win wlan symbol (bars)!!! In both cases you do not see a change in the task bar it is always the same icon.  And if you want to install another OS after a Linux installation on this notebook, you can work with the internal bootmanager from HP which is implemented in the BIOS. cheers jojo

---

