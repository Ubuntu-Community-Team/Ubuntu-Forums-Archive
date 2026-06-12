---
title: "Wireless up but not working (tried NM 0.7.0 and Wicd)"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by AngelX on 2008-10-07
Hi, I'm having trouble with the wireless (like many others)... Network Manger was not working as it kept asking for the network WEP key, it tried to connect but never did. I have an atheros card. I've recently changed the network manager to Wicd and this time Wicd doesn't see any wireless networks (altough the iwlist scan sees them). Have no clue what's going on, good thing is hard wire network is working; appreciate the help.

Find below the results of (I saw in other post that this gives a clue to find out the problem):

* lshw -C Network
* lspci -nn
* dmesg | grep -e iwl -e wlan -e rt -e ath
* ifconfig
* sudo iwlist scan

```

lshw -C Network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:cb:e2:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.65 latency=64 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7e:02:50:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:c4:84:d3:2c:8d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

lspci -nn (I remove the other crap and left only the wireless)
06:02.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)

dmesg | grep -e iwl -e wlan -e rt -e ath
angelo@angelo-laptop:~$ dmesg | grep -e iwl -e wlan -e rt -e ath
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.004000] virtual kernel memory layout:
[    1.056391] Booting paravirtualized kernel on bare hardware
[    1.096133] ACPI: (supports S0 S3 S4 S5)
[    1.212953] ACPI: EC: driver started in poll mode
[    1.212953] PCI: 0000:00:02.0 reg 14 io port: [5088, 508f]
[    1.212953] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.212953] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.212993] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.213137] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.213281] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.213391] PCI: 0000:00:1d.0 reg 20 io port: [50a0, 50bf]
[    1.216039] PCI: 0000:00:1d.1 reg 20 io port: [50c0, 50df]
[    1.216156] PCI: 0000:00:1d.2 reg 20 io port: [50e0, 50ff]
[    1.216272] PCI: 0000:00:1d.3 reg 20 io port: [5400, 541f]
[    1.216501] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.216895] PCI: 0000:00:1f.2 reg 10 io port: [0, 7]
[    1.216916] PCI: 0000:00:1f.2 reg 14 io port: [0, 3]
[    1.216936] PCI: 0000:00:1f.2 reg 18 io port: [0, 7]
[    1.216956] PCI: 0000:00:1f.2 reg 1c io port: [0, 3]
[    1.216977] PCI: 0000:00:1f.2 reg 20 io port: [5440, 544f]
[    1.217039] pci 0000:00:1f.2: PME# supported from D3hot
[    1.217150] PCI: 0000:00:1f.3 reg 20 io port: [5420, 543f]
[    1.217319] PCI: bridge 0000:00:1c.0 io port: [0, fff]
[    1.217893] pci 0000:06:01.0: supports D1
[    1.217901] pci 0000:06:01.0: supports D2
[    1.217911] pci 0000:06:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.218210] pci 0000:06:04.0: supports D1
[    1.218219] pci 0000:06:04.0: supports D2
[    1.218229] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.218428] pci 0000:06:04.1: supports D1
[    1.218437] pci 0000:06:04.1: supports D2
[    1.218446] pci 0000:06:04.1: PME# supported from D0 D1 D2 D3hot
[    1.218639] pci 0000:06:04.2: supports D1
[    1.218648] pci 0000:06:04.2: supports D2
[    1.218658] pci 0000:06:04.2: PME# supported from D0 D1 D2 D3hot
[    1.218853] pci 0000:06:04.3: supports D1
[    1.218862] pci 0000:06:04.3: supports D2
[    1.218872] pci 0000:06:04.3: PME# supported from D0 D1 D2 D3hot
[    1.219067] pci 0000:06:04.4: supports D1
[    1.219075] pci 0000:06:04.4: supports D2
[    1.219085] pci 0000:06:04.4: PME# supported from D0 D1 D2 D3hot
[    1.251005] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.332233] system 00:06: ioport range 0x1000-0x107f has been reserved
[    1.332247] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    1.332262] system 00:06: ioport range 0x1640-0x164f has been reserved
[    1.332276] system 00:06: ioport range 0xfe00-0xfefe has been reserved
[    1.332291] system 00:06: ioport range 0xff2c-0xff2f has been reserved
[    1.369939] bus: 00 index 0 io port: [0, ffff]
[    1.370107] bus: 06 index 0 io port: [2000, 2fff]
[    1.370139] bus: 06 index 3 io port: [0, ffff]
[    1.370159] bus: 07 index 0 io port: [2000, 20ff]
[    1.370170] bus: 07 index 1 io port: [2400, 24ff]
[    3.291162] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    3.291236] pcieport-driver 0000:00:1c.0: found MSI capability
[    3.291314] pci_express 0000:00:1c.0:pcie00: allocate port service
[    3.291423] pci_express 0000:00:1c.0:pcie02: allocate port service
[    3.291526] pci_express 0000:00:1c.0:pcie03: allocate port service
[    3.291740] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    3.291810] pcieport-driver 0000:00:1c.1: found MSI capability
[    3.291881] pci_express 0000:00:1c.1:pcie00: allocate port service
[    3.291985] pci_express 0000:00:1c.1:pcie02: allocate port service
[    3.292106] pci_express 0000:00:1c.1:pcie03: allocate port service
[    3.292317] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    3.292387] pcieport-driver 0000:00:1c.2: found MSI capability
[    3.292458] pci_express 0000:00:1c.2:pcie00: allocate port service
[    3.292578] pci_express 0000:00:1c.2:pcie02: allocate port service
[    3.292693] pci_express 0000:00:1c.2:pcie03: allocate port service
[    3.292905] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    3.292975] pcieport-driver 0000:00:1c.3: found MSI capability
[    3.293056] pci_express 0000:00:1c.3:pcie00: allocate port service
[    3.293177] pci_express 0000:00:1c.3:pcie02: allocate port service
[    3.293288] pci_express 0000:00:1c.3:pcie03: allocate port service
[    3.724986] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.731596] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.731610] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.731617] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.731624] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.731630] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.732667] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    3.732716] rtc0: alarms up to one month, y3k, hpet irqs
[    3.734455] Using IPI No-Shortcut mode
[    3.735409] rtc_cmos 00:07: setting system clock to 2008-10-07 01:06:13 UTC (1223341573)
[    4.341117] ACPI: Processor [CPU0] (supports 8 throttling states)
[    4.345319] ACPI: Processor [CPU1] (supports 8 throttling states)
[    5.882814] hub 1-0:1.0: 2 ports detected
[    5.989007] hub 2-0:1.0: 2 ports detected
[    6.200949] hub 3-0:1.0: 2 ports detected
[    6.301098] hub 4-0:1.0: 2 ports detected
[    6.410967] ehci_hcd 0000:00:1d.7: debug port 1
[    6.410981] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    6.460039] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.460465] hub 5-0:1.0: 8 ports detected
[    6.912139] hub 2-0:1.0: unable to enumerate USB device on port 2
[    7.342868] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.343264] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.266518] kjournald starting.  Commit interval 5 seconds
[   23.275451] udevd version 124 started
[   25.738518] Linux agpgart interface v0.103
[   25.761580] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   25.762274] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   25.918053] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   28.713126] ath5k_pci 0000:06:02.0: enabling device (0000 -> 0002)
[   28.713148] ath5k_pci 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   28.713370] ath5k_pci 0000:06:02.0: registered as 'phy0'
[   29.430753] iTCO_vendor_support: vendor-support=0
[   29.452464] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.172548] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   30.406312] cs: IO port probe 0x2000-0x2fff: clean.
[   30.491633] ath_hal: module license 'Proprietary' taints kernel.
[   30.501397] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   30.540516] wlan: 0.9.4
[   30.556264] ath_pci: 0.9.4
[   31.067319] cs: IO port probe 0x100-0x3af: clean.
[   31.069721] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   31.070713] cs: IO port probe 0x820-0x8ff: clean.
[   31.071526] cs: IO port probe 0xc00-0xcf7: clean.
[   31.072598] cs: IO port probe 0xa00-0xaff: clean.
[   69.285957] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   69.664956] ppdev: user-space parallel port driver
[  668.449267] ADDRCONF(NETDEV_UP): wlan0: link is not ready

ifconfig
angelo@angelo-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:cb:e2:59  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fecb:e259/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2644514 (2.6 MB)  TX bytes:407305 (407.3 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2565 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:131660 (131.6 KB)  TX bytes:131660 (131.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:02:50:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7E-02-50-02-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwlist scan
angelo@angelo-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:5B:E5:12:41
                    ESSID:"INFINITUM0948"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/100  Signal level:-64 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000137bd82271
                    Extra: Last beacon: 908ms ago
          Cell 02 - Address: 00:18:3F:BD:3F:11
                    ESSID:"Angelo"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=90/100  Signal level:-36 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000000d44e0181
                    Extra: Last beacon: 460ms ago
pan0      Interface doesn't support scanning.
```

---

### Post by ELD on 2008-10-07
Same problems here it will not connect even to a unsecured network.

---

### Post by zbrox on 2008-10-07
Just a "me too" reply. The problem is on a Dell Vostro 1310 with Broadcom WiFi card, which was working OK under 8.04, with the proprietary "wl" driver.

---

### Post by executor on 2008-10-07
maybe this will help?

have you checkt that the /etc/NetworkManager/nm-system-settings.conf, is sett to managed=true 

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

mine was sett to false.

---

### Post by ELD on 2008-10-07
> **executor said:**
> maybe this will help?

have you checkt that the /etc/NetworkManager/nm-system-settings.conf, is sett to managed=true 

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

mine was sett to false.

And checking that enabled you to connect to your wireless?

---

### Post by executor on 2008-10-07
> **ELD said:**
> And checking that enabled you to connect to your wireless?

yes

---

### Post by AdrianVeidt on 2008-10-07
Atheros drivers are not supported fully in Network-Manager .70. There has been an open bug about this for some time. This behaviour covers both the ath5k (for non wireless-n devices) and the ath9k (for wireless-n only) drivers. 
There are some devices they'll connect to, and some they won't. The bug was supposed to be fixed by Beta 1, but has been pushed back to the final release (in 2 weeks).
The bug is [LP #259157 [MASTER 0.7 regression] atheros/madwifi and orinoco drivers not supported]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259157")
Fixing this bug is essential to releasing Intrepid in a usable state because Atheros wireless chips drive so many wifi devices, and this bug affects everyone, even some people who don't realize it because they're connecting to one of the routers that the current drivers have no problem with.

---

