---
title: "Dell Vostro v130"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by Frankiewizard on 2012-10-29
Hello people have been using a dell vostro v130 64 bits with 12.04 for a month or two. No problems until yesterday connecting to the wi-fi seems a no go. Direct link to the Internet box works.
Any suggestions Cheers.

---

### Post by Frankiewizard on 2012-10-29
I think the following information may be of use
Cheers..........


```
cat /etc/lsb-release 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```

```
lsusb
12:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
```

```
lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
	Subsystem: Dell Device 049c
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
	Subsystem: Dell Device 049c
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Dell Device 049c
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
	Subsystem: Dell Device 049c
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Dell Device 049c
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
	Subsystem: Dell Device 049c
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: Dell Device 049c
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
	Subsystem: Dell Device 049c
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
	Subsystem: Dell Device 049c
	Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
	Subsystem: Dell Device 049c
	Kernel modules: intel_ips
12:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Dell Wireless 1702 802.11bgn Half-size Mini PCIe Card [AR9002WB-1NGCD]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Dell Device 049c
	Kernel driver in use: r8169
	Kernel modules: r8169
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
```

```
lspci -k
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 01
       serial: cc:af:78:8b:e0:47
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-32-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fe400000-fe40ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 06
       serial: 18:03:73:60:6e:eb
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
```

```

sudo lshw -C network
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
uas                    18180  0 
usb_storage            49198  0 
joydev                 17693  0 
rfcomm                 47604  0 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
binfmt_misc            17540  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
ath9k                 132390  0 
psmouse                97443  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath3k                  12961  0 
btusb                  18288  1 
mac80211              506816  1 ath9k
intel_ips              18174  0 
serio_raw              13211  0 
bluetooth             180104  14 rfcomm,bnep,ath3k,btusb
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           14053  1 ath9k
ath9k_hw              411151  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
i915                  473298  3 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 dell_wmi
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46978  1 i915
soundcore              15091  1 snd
mac_hid                13253  0 
drm                   241921  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
mei                    41616  0 
video                  19596  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
```

```

lsmod
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
```

```
iwconfig
wlan0     Link encap:Ethernet  HWaddr cc:af:78:8b:e0:47  
          inet6 addr: fe80::ceaf:78ff:fe8b:e047/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34720 (34.7 KB)  TX bytes:231129 (231.1 KB)
```

```

ifconfig
wlan0     Scan completed :
          Cell 01 - Address: 1A:BA:9D:9F:81:D6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012af90442c
                    Extra: Last beacon: 288ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000500000000000000000000000000000000000000
          Cell 02 - Address: 1A:BA:9D:9F:81:D4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"HSH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012af903171
                    Extra: Last beacon: 292ms ago
                    IE: Unknown: 0003485348
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000500000000000000000000000000000000000000
          Cell 03 - Address: 1A:BA:9D:9F:81:D5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012af903af3
                    Extra: Last beacon: 288ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040049127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000500000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 04 - Address: 00:24:D4:98:57:50
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"freebox"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016c408012c1
                    Extra: Last beacon: 560ms ago
                    IE: Unknown: 000766726565626F78
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:1A:2B:49:78:F5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"NUMERICABLE-B104"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005e87d986008
                    Extra: Last beacon: 544ms ago
                    IE: Unknown: 00104E554D4552494341424C452D42313034
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180204F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 00:24:D4:98:57:51
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016c407fa66d
                    Extra: Last beacon: 552ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 07 - Address: 00:24:D4:98:57:52
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016c407f2dd3
                    Extra: Last beacon: 552ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 08 - Address: 1A:BA:9D:9F:81:D7
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012af904cf6
                    Extra: Last beacon: 284ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000500000000000000000000000000000000000000
          Cell 09 - Address: 00:24:D4:DA:73:9C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Ladychabine972"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000143da230160
                    Extra: Last beacon: 336ms ago
                    IE: Unknown: 000E4C61647963686162696E65393732
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 10 - Address: 00:16:CF:6B:2C:DB
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Livebox-52E0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002457fb778b9
                    Extra: Last beacon: 820ms ago
                    IE: Unknown: 000C4C697665626F782D35324530
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: 6A:12:F8:A9:B9:50
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"freebox_JV"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f3f9ea3150
                    Extra: Last beacon: 476ms ago
                    IE: Unknown: 000A66726565626F785F4A56
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1608050000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500008C127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3408050000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 12 - Address: 6A:25:15:BC:C6:11
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"SFR WiFi Public"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000495f421245
                    Extra: Last beacon: 912ms ago
                    IE: Unknown: 000F5346522057694669205075626C6963
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 13 - Address: D0:AE:EC:21:0D:97
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Livebox-6df2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019d1a8c119c
                    Extra: Last beacon: 632ms ago
                    IE: Unknown: 000C4C697665626F782D36646632
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD2C0050F204104A00011010440001021057000100104700106C2E85326DF26C2E85326DF285326DF2103C000101
          Cell 14 - Address: E8:BE:81:17:8D:8C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Livebox-8d8c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f99d2c180
                    Extra: Last beacon: 624ms ago
                    IE: Unknown: 000C4C697665626F782D38643863
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018E0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 15 - Address: F4:CA:E5:CB:A4:7D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005d512628160
                    Extra: Last beacon: 340ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 16 - Address: D2:25:15:A9:EF:2F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"SFR WiFi Mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d64dd775e8
                    Extra: Last beacon: 316ms ago
                    IE: Unknown: 000F5346522057694669204D6F62696C65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

```

```

sudo iwlist scan
auto lo
iface lo inet loopback
```

```
uname -r -m 
phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
6: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
```

---

### Post by kanikilu on 2012-10-29
I think the output of your commands is in the wrong order - for instance the output to the lshw command is listed under lspci ...

Anyways, the wirless adapter is showing "DISABLED". I think the most common reason for that, is a physical switch to toggle your wireless card on and off. Does your laptop have one of these switches? If so, try toggling it. Other laptops may have a button somewhere on the keyboard (may be a Fn+Key combo) to do the same thing.

If you don't have a hardware switch, and the Fn key combo doesn't work, do you dual-boot? If so, the Ubuntu wireless networking troubleshooting guide suggests trying to enable the adapter in Windows.

If you don't dual boot, the only other suggestions I'd have are:

1) Look in the BIOS (usually F2 during POST on a Dell) to see if the adapter can be enabled in there.

2) Shutdown, unplug the laptop, take out the battery, and then press and hold the power button for several seconds. Then put it back together and boot up.

The strange thing is that **rfkill list** isn't showing that the adapter is blocked, so I may be barking up the wrong tree here... :confused:

---

### Post by Frankiewizard on 2012-10-29
Cheers
(1) I am not on a double boot system just 12.04 UbuntU. W****** gives me spots
(2) and I think that the switch for the wi-fi may have been off by mistake when I did the test :(
(3) I will re do the test

---

### Post by Frankiewizard on 2012-10-29
This is what I found when I re did the test.

Cheers

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

---

### Post by Frankiewizard on 2012-10-30
In fact what I have found is that the wi-fi is working the problem is that I can not connect to my proper internet box. It works fine with all sorts of other internet boxes but not the one I have at home.

So I think that I have been indeed barking up the wrong tree.

Thanks for your help.

---

