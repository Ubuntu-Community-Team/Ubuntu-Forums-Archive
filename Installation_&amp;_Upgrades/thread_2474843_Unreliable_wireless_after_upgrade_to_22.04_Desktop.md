---
title: "Unreliable wireless after upgrade to 22.04 Desktop"
date: 2022-05-09
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2022-05-09
My wireless connection worked reliably until I upgraded to 22.04.

It now restarts  regularly 'stuffing' up all apps that rely on the internet in the progress.

wpa_supplicant reports CTRL-EVENT-BEACON-LOSS (see attached log)

$ lshw -C network

```
 *-network                 
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 01
       serial: 6c:71:d9:8b:5c:7d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=5.15.0-27-generic firmware=N/A ip=192.168.1.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:ff600000-ff67ffff memory:ff680000-ff68ffff
  *-network
       description: Ethernet interface
       product: QCA8171 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 10
       serial: d0:50:99:00:b5:2b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=5.15.0-27-generic latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:ff500000-ff53ffff ioport:e000(size=128)

```

$ watch sudo iwlist wlp1s0 scan

```
Every 2.0s: sudo iwlist wlp1s0 scan                                                          ingesDesktop1: Tue May 10 09:41:44 2022

wlp1s0    Scan completed :
          Cell 01 - Address: 60:A4:B7:7C:5B:A2
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=68/70  Signal level=-42 dBm
                    Encryption key:on
                    ESSID:"thelists_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001bb50de1aa6
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000C7468656C697374735F455854
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEE111BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D16040D0400000000000000000000000000000000000000
                    IE: Unknown: 7F080400000200000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD168CFDF0040000494C510302097201000000003F000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD088CFDF00101020100
          Cell 02 - Address: 60:A4:B7:7C:5B:A1
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=52/70  Signal level=-58 dBm
                    Encryption key:on
                    ESSID:"thelists-5G_EXT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s

```


Thanks

---

