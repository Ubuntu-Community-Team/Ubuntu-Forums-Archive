---
title: "Unable get E372 Huawei Mobile Broadband to connect to internet"
date: 2017-01-04
forum: MINT
---

### Post by belbelli on 2017-01-04
Hello Everyboby,
I'm struggling with an Huawei E372 usb internet key and I cannot let it work.
I searched and googled my problem but I cannot find any final solution.
I give you some info about my status:
command ***lsusb*** gives:

```
Bus 001 Device 004: ID 12d1:1505 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
```

***dmesg***:

```
[   11.358080] scsi 3:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[   11.358413] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   11.358572] scsi 2:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   11.363729] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   11.364395] sr 2:0:0:0: [sr1] scsi-1 drive
[   11.364583] sr 2:0:0:0: Attached scsi CD-ROM sr1
[   11.365006] sr 2:0:0:0: Attached scsi generic sg3 type 5
[   11.476071] Adding 3999740k swap on /dev/sda6.  Priority:-1 extents:1 across:3999740k FS
```

command:  ***sudo usb-modeswitch -H -v  0x12d1 -p 0x1505 -W***:

```
Take all parameters from the command line


 * usb_modeswitch: handle USB devices with multiple modes
 * Version 2.2.5 (C) Josua Dietze 2015
 * Based on libusb1/libusbx

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x12d1
DefaultProduct= 0x1505
HuaweiMode=1
NeedResponse=0

Look for default devices ...
  found USB ID 1d6b:0003
  found USB ID 0c45:651b
  found USB ID 0bda:b006
  found USB ID 12d1:1505
   vendor ID matched
   product ID matched
  found USB ID 1d6b:0002
 Found devices in default mode (1)
Access device 004 on bus 001
Current configuration number is 1
Use interface number 0

USB description data (for identification)
-------------------------
Manufacturer: Huawei Technologies
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Send old Huawei control message ...
Error: Huawei control message failed (error -9). Abort
```

What I cannot understand is why I cannot see my mobile broadband connection in the networkmanager?
usb-modeswitch and usb-modeswitch-data are installed.
Any hint? Something more to check?

Thanks,
Luca

---

### Post by ajgreeny on 2017-01-04
See Wireless-info in my signature and follow the instruction there to run it and paste the result you get back here, either using a pastebin link or using code tags.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by belbelli on 2017-01-05
Hello ajgreeny,
I updated my distro but still I have the problem.
I run the script wireless-info, I read the file but I cannot see any info for my problem.
Can you please help me out with this?
Here you have the output of the script:

```

########## wireless info START ##########

Report from: 05 Jan 2017 08:45 CET +0100

Booted last: 05 Jan 2017 00:00 CET +0100

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 18 Sarah
Release:    18
Codename:    sarah

##### kernel ############################

Linux 4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:80c1]
    Kernel driver in use: r8169

0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0c45:651b Microdia 
Bus 001 Device 002: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 12d1:1505 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             143360  0
btcoexist             299008  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               135168  3 btcoexist,rtl_pci,rtl8723be
mac80211              737280  3 rtl_pci,rtlwifi,rtl8723be
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
snd_soc_rt286          36864  0
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_soc_core          212992  2 snd_soc_ssm4567,snd_soc_rt286
cfg80211              565248  2 mac80211,rtlwifi
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp7s0    Link encap:Ethernet  HWaddr <MAC 'enp7s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp13s0   Link encap:Ethernet  HWaddr <MAC 'wlp13s0' [IF2]>  
          inet addr:192.168.43.130  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::6d6b:6133:b100:6a38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1771755 (1.7 MB)  TX bytes:284928 (284.9 KB)

##### iwconfig ##########################

enp7s0    no wireless extensions.

lo        no wireless extensions.

wlp13s0   IEEE 802.11bgn  ESSID:"G2 mini_2370"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'G2 mini_2370' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-14 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    600    0        0 wlp13s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp13s0
192.168.43.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp13s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       864     1  0 08:39 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp13s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.4.0-43-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp13s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:0d:00.0/net/wlp13s0
GENERAL.IP-IFACE:                       wlp13s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto G2 mini_2370
GENERAL.CON-UUID:                       7049b83f-d87b-4cc1-ba45-7b275a47b8fd
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7049b83f-d87b-4cc1-ba45-7b275a47b8fd | Auto G2 mini_2370
IP4.ADDRESS[1]:                         192.168.43.130/24
IP4.GATEWAY:                            192.168.43.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.43.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.43.1
DHCP4.OPTION[5]:                        ip_address = 192.168.43.130
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.43.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.43.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 6300
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.43.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 3600
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1483609460
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = BeLLiPC
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.43.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.43.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 7200
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::6d6b:6133:b100:6a38/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp7s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp7s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:07:00.0/net/enp7s0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0a6d3920-5bfc-474c-a6bc-4f837b4cf00a | Profile 1

SSID                  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
G2 mini_2370          <MAC 'G2 mini_2370' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         yes     * 
Telecom-86554379      <MAC 'Telecom-86554379' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
Telecom-94398455      <MAC 'Telecom-94398455' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
FRITZ!Box 3272        <MAC 'FRITZ!Box 3272' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
DIRECT-VIC48x Series  <MAC 'DIRECT-VIC48x Series' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2       no        
Padovaclima WiFi      <MAC 'Padovaclima WiFi' [AN6]>  Infra  1     2412 MHz  48 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/Auto BeLLi]] (600 root)
[connection] id=Auto BeLLi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp13s0' [IF2]> | mac-address-blacklist= | ssid=BeLLi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto G2 mini_2370]] (600 root)
[connection] id=Auto G2 mini_2370 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp13s0' [IF2]> | mac-address-blacklist= | ssid=G2 mini_2370
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto Windows Phone8965]] (600 root)
[connection] id=Auto Windows Phone8965 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp13s0' [IF2]> | mac-address-blacklist= | ssid=Windows Phone8965
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Rome (based on set time zone)

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

enp7s0    no frequency information.

lo        no frequency information.

wlp13s0   13 channels in total; available frequencies :
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
          Current Frequency:2.417 GHz (Channel 2)

##### iwlist scan #######################

enp7s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp13s0   Scan completed :
          Cell 01 - Address: <MAC 'G2 mini_2370' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:off
                    ESSID:"G2 mini_2370"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000084b969e
                    Extra: Last beacon: 128ms ago
          Cell 02 - Address: <MAC 'Telecom-94398455' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Telecom-94398455"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000025f4b8d618
                    Extra: Last beacon: 160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'FRITZ!Box 3272' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 3272"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000412183613f9
                    Extra: Last beacon: 1852ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Telecom-86554379' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Telecom-86554379"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ca1a1622f
                    Extra: Last beacon: 23868ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'DIRECT-VIC48x Series' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-VIC48x Series"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000025f0dbcc33
                    Extra: Last beacon: 3872ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.4.0-43-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     2DA37D00E0E770F2130B511
depends:        rtl_pci,rtlwifi,btcoexist,mac80211
vermagic:       4.4.0-42-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-43-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     373C318E7A4A30F203D0283
depends:        mac80211,rtlwifi
vermagic:       4.4.0-42-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-43-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8C835F6B10D8DF1B731CA85
depends:        mac80211,cfg80211
vermagic:       4.4.0-42-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-43-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-43-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
ant_sel: 2
debug: 1
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
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

[/etc/modprobe.d/50-rtl8723be.conf]
options rtl8723be ant_sel=2

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

rfkill block bluetooth
exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   10.672937] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   10.672941] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   11.090210] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   11.297937] Using firmware rtlwifi/rtl8723befw.bin
[   11.348544] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.349147] rtlwifi: wireless switch is on
[   11.463069] rtl8723be 0000:0d:00.0 wlp13s0: renamed from wlan0
[   19.548355] IPv6: ADDRCONF(NETDEV_UP): wlp13s0: link is not ready (repeated 2 times)
[   20.089371] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
[   20.201155] r8169 0000:07:00.0 enp7s0: link down
[   20.201241] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
[   20.997440] IPv6: ADDRCONF(NETDEV_UP): wlp13s0: link is not ready
[  303.371751] wlp13s0: authenticate with <MAC 'G2 mini_2370' [AC1]>
[  303.383315] wlp13s0: send auth to <MAC 'G2 mini_2370' [AC1]> (try 1/3)
[  303.388457] wlp13s0: authenticated
[  303.392573] wlp13s0: associate with <MAC 'G2 mini_2370' [AC1]> (try 1/3)
[  303.407573] wlp13s0: RX AssocResp from <MAC 'G2 mini_2370' [AC1]> (capab=0x8421 status=0 aid=1)
[  303.408451] wlp13s0: associated
[  303.408465] IPv6: ADDRCONF(NETDEV_CHANGE): wlp13s0: link becomes ready

########## wireless info END ############


```

In attachment you can find the .txt and the .tar.gz output as well.

Thanks,
Luca

---

### Post by ajgreeny on 2017-01-05
*Thread moved to **MINT**.* which is more appropriate for the problem and should be a better fit.

I regret that my wifi knowledge is not good enough to help you, but I hope others will be along who can help you more than I can.

---

### Post by belbelli on 2017-01-08
no one can help me out with this?

---

### Post by jeremy31 on 2017-01-08
I would try ```
eject /dev/sr1
```
See if it becomes usuable then also see if ```
usb_modeswitch -v12d1 -p1505 -J
```
Does the job, found at [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=3&t=2619](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=3&t=2619)

---

### Post by chaitanyaarige on 2017-01-20
Thanks Bro.....U are awesome
Its working.... 
I am using EC306-I model. But has same Vendor ID and product ID

usb_modeswitch -v12d1 -p1505 -J

---

