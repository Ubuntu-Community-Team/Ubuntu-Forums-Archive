---
title: "Wireless broken by 10.04 beta 2 upgrade from 9.10 on EeePC 901"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bonsty on 2010-04-14
Hi, the issue I am having is with connecting to wireless networks with my eepc 901, I'm running the ubuntu 10.04 beta 2. The wireless card that I'm using was working fine with 9.10, I am able to scan for networks but the machine is unable to connect. I have tried both b,g and n networks with no success. I have included the appropriate information below and would be very grateful to any help that anyone is willing to give me.
Regards,
Matt.



1 ) Machine Brand and Model (PC/Laptop):
eeePC 901


2 ) Wireless Brand, Model and Wireless Chipset:
Code:
01:00.0 Network controller: RaLink RT2860
        Subsystem: RaLink Device 2790
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fbef0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2860
        Kernel modules: rt2860sta

3 ) check interface:
wlan0     Link encap:Ethernet  HWaddr 00:15:af:e4:f6:aa  
          inet6 addr: fe80::215:afff:fee4:f6aa/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:65663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11425233 (11.4 MB)  TX bytes:3078 (3.0 KB)
          Interrupt:19 

4 ) Check for modules:
rt2860sta             481849  1 

5 ) Kernel boot messages
Code:
[   10.749822] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.

6 ) Network configuration
2.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:fbfc0000-fbffffff ioport:ec80(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:15:af:e4:f6:aa
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:fbef0000-fbefffff

7 ) Scan for networks:

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:28:FC:22
                    Protocol:802.11g
                    ESSID:"constable1"
                    Mode:Managed
                    Channel:6
                    Quality:76/100  Signal level:-60 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:12:BF:00:6E:F9
                    Protocol:802.11b/g
                    ESSID:"williams"
                    Mode:Managed
                    Channel:11
                    Quality:60/100  Signal level:-66 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1E:2A:12:6F:80
                    Protocol:802.11b/g
                    ESSID:"starkie"
                    Mode:Managed
                    Channel:11
                    Quality:10/100  Signal level:-86 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


8 ) Ubuntu Version: 
Description:	Ubuntu lucid (development branch)

9 ) Kernel/architecture (including 32 vs. 64 bit): 
Code:
2.6.32-20-generic i686

10 ) Restarting the network:
 * Reconfiguring network interfaces...                                                                                       Ignoring unknown interface eth0=eth0.
                                                                                                                      [ OK ]

---

### Post by matthewbpt on 2010-04-14
Open a bug on Launchpad about this, this way you'll be sure developers will see the problem. Most of them don't have tome to come on the forums. My wireless is working at the moment on my EeePC 901. It gave a little trouble connecting at first but now seems to connect fine.

---

### Post by eltonw on 2010-04-14
> **bonsty said:**
> Hi, the issue I am having is with connecting to wireless networks with my eepc 901, I'm running the ubuntu 10.04 beta 2. The wireless card that I'm using was working fine with 9.10, I am able to scan for networks but the machine is unable to connect. I have tried both b,g and n networks with no success. I have included the appropriate information below and would be very grateful to any help that anyone is willing to give me.
Regards,
Matt.



1 ) Machine Brand and Model (PC/Laptop):
eeePC 901


2 ) Wireless Brand, Model and Wireless Chipset:
Code:
01:00.0 Network controller: RaLink RT2860
        Subsystem: RaLink Device 2790
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fbef0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2860
        Kernel modules: rt2860sta

3 ) check interface:
wlan0     Link encap:Ethernet  HWaddr 00:15:af:e4:f6:aa  
          inet6 addr: fe80::215:afff:fee4:f6aa/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:65663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11425233 (11.4 MB)  TX bytes:3078 (3.0 KB)
          Interrupt:19 

4 ) Check for modules:
rt2860sta             481849  1 

5 ) Kernel boot messages
Code:
[   10.749822] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.

6 ) Network configuration
2.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:fbfc0000-fbffffff ioport:ec80(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:15:af:e4:f6:aa
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:fbef0000-fbefffff

7 ) Scan for networks:

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:28:FC:22
                    Protocol:802.11g
                    ESSID:"constable1"
                    Mode:Managed
                    Channel:6
                    Quality:76/100  Signal level:-60 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:12:BF:00:6E:F9
                    Protocol:802.11b/g
                    ESSID:"williams"
                    Mode:Managed
                    Channel:11
                    Quality:60/100  Signal level:-66 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1E:2A:12:6F:80
                    Protocol:802.11b/g
                    ESSID:"starkie"
                    Mode:Managed
                    Channel:11
                    Quality:10/100  Signal level:-86 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


8 ) Ubuntu Version: 
Description:	Ubuntu lucid (development branch)

9 ) Kernel/architecture (including 32 vs. 64 bit): 
Code:
2.6.32-20-generic i686

10 ) Restarting the network:
 * Reconfiguring network interfaces...                                                                                       Ignoring unknown interface eth0=eth0.
                                                                                                                      [ OK ]

**[FONT="Arial Black"]FYI:[/FONT]** [COLOR="Red"]
One should [SIZE="4"]_*NOT*_[/SIZE] "upgrade" with [COLOR="DarkRed"]*_BETA_*[/COLOR] code.

[CENTER][/COLOR][FONT="Comic Sans MS"] Betas are meant for _testing_, and _things may / normally / usually break.[/FONT]_[/CENTER]

That said, [SIZE="3"]the discussion of [COLOR="DarkRed"]LUCID BETA connectivity problems is[/COLOR] _**at this link**_[/SIZE]: 
[http://ubuntuforums.org/showthread.php?t=1438175]("http://ubuntuforums.org/showthread.php?t=1438175")

---

