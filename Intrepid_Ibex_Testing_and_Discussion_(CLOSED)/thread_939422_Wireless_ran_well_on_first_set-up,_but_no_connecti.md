---
title: "Wireless ran well on first set-up, but no connection thereafter"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kvk on 2008-10-05
I just bought a new custom-built computer for audio processing. I loaded 8.04, then immediately upgraded to Ibex. Everything went smoothly and very well. Wireless initially connected on set-up using NM with no problem. However, after rebooting, although the ESSID in listed in NM, and it detectes the router when a connection is initiated, it returns "The network connection has been disconnected". In addition, the selection for "Wireless Networks" is grayed out in the initial NM drop-down menu. I have to use "Create New Wireless Network" to generate the connection, even though it only lasts ten seconds.

In the terminal, using

sudo iwconfig wmaster0 essid "NETWORKNAME"

returns 

Error for wireless request "Set ESSID" (8B1A):
SET failed on device master wmaster0; Operation not supported"

I've been very pleased with everything else so far in Ibex, much more so than Hardy. If I can solve this it would be most excellent!!

---

### Post by pytheas22 on 2008-10-05
Please open a terminal and post the output of the following:

```
lshw -C Network
lspci -nn
dmesg | grep -e iwl -e wlan -e rt -e ath
ifconfig
sudo iwlist scan
```

so that we can diagnose the problem.

---

### Post by dunbrokin on 2008-10-06
> **pytheas22 said:**
> Please open a terminal and post the output of the following:

```
lshw -C Network
lspci -nn
dmesg | grep -e iwl -e wlan -e rt -e ath
ifconfig
sudo iwlist scan
```

so that we can diagnose the problem.

I have a similar problem and here is my readout...

fitz@fitz-laptop:~$ sudo lshw -C Network 
  *-network               
       description: Ethernet interface 
       product: 3c556B CardBus [Tornado] 
       vendor: 3Com Corporation 
       physical id: 3 
       bus info: pci@0000:00:03.0 
       logical name: eth0 
       version: 20 
       serial: 00:04:76:60:6f:87 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s 
  *-network DISABLED 
       description: Wireless interface 
       product: ACX 111 54Mbps Wireless Interface 
       vendor: Texas Instruments 
       physical id: 1 
       bus info: pci@0000:06:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:0f:3d:57:76:56 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+ 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: d2:f8:de:93:ae:85 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
fitz@fitz-laptop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03) 
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03) 
00:02.0 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03) 
00:02.1 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03) 
00:03.0 Ethernet controller [0200]: 3Com Corporation 3c556B CardBus [Tornado] [10b7:6056] (rev 20) 
00:03.1 Communication controller [0780]: 3Com Corporation Mini PCI 56k Winmodem [10b7:1007] (rev 20) 
00:05.0 Multimedia audio controller [0401]: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] [1013:6003] (rev 01) 
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02) 
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01) 
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01) 
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03) 
01:00.0 VGA compatible controller [0300]: S3 Inc. 86C270-294 Savage/IX-MV [5333:8c12] (rev 13) 
06:00.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066] 
fitz@fitz-laptop:~$ dmseg | grep -e iwl -e wlan -e rt -e ath 
bash: dmseg: command not found 
fitz@fitz-laptop:~$ dmesg | grep -e iwl -e wlan -e rt -e ath 
[    0.000000] Movable zone start PFN for each node 
[    0.000000] ACPI: PM-Timer IO Port: 0x1008 
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000) 
[    0.000000] Enabling unmasked SIMD FPU exception support... done. 
[    0.004000] virtual kernel memory layout: 
[    0.881353] Booting paravirtualized kernel on bare hardware 
[    1.365536] ACPI: (supports S0 S1 S3 S4 S5) 
[    1.626629] ACPI: EC: driver started in interrupt mode 
[    1.628743] pci 0000:00:02.0: supports D1 
[    1.628753] pci 0000:00:02.0: supports D2 
[    1.628764] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    1.628864] pci 0000:00:02.1: supports D1 
[    1.628873] pci 0000:00:02.1: supports D2 
[    1.628883] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold 
[    1.628959] PCI: 0000:00:03.0 reg 10 io port: [1800, 18ff] 
[    1.629065] pci 0000:00:03.0: supports D1 
[    1.629074] pci 0000:00:03.0: supports D2 
[    1.629085] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    1.629149] PCI: 0000:00:03.1 reg 10 io port: [2000, 20ff] 
[    1.629243] pci 0000:00:03.1: supports D2 
[    1.629254] pci 0000:00:03.1: PME# supported from D0 D2 D3hot D3cold 
[    1.629413] pci 0000:00:05.0: supports D1 
[    1.629422] pci 0000:00:05.0: supports D2 
[    1.629561] PCI: 0000:00:07.1 reg 20 io port: [1c00, 1c0f] 
[    1.629659] PCI: 0000:00:07.2 reg 20 io port: [1c20, 1c3f] 
[    1.630050] pci 0000:01:00.0: supports D1 
[    1.630060] pci 0000:01:00.0: supports D2 
[    1.672879] Linux Plug and Play Support v0.97 (c) Adam Belay 
[    1.804694] system 00:02: ioport range 0x1000-0x103f has been reserved 
[    1.804709] system 00:02: ioport range 0x1040-0x104f has been reserved 
[    1.804725] system 00:02: ioport range 0xfe00-0xfe0f has been reserved 
[    1.804778] system 00:09: ioport range 0x15e0-0x15ef has been reserved 
[    1.848667] bus: 00 index 0 io port: [0, ffff] 
[    1.848730] bus: 02 index 0 io port: [1400, 14ff] 
[    1.848741] bus: 02 index 1 io port: [2400, 24ff] 
[    1.848774] bus: 06 index 0 io port: [2800, 28ff] 
[    1.848784] bus: 06 index 1 io port: [2c00, 2cff] 
[    4.290293] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
[    4.320603] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    4.320626] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    4.322535] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0 
[    4.322574] rtc0: alarms up to one month, y3k 
[    4.324893] Using IPI No-Shortcut mode 
[    4.326596] rtc_cmos 00:06: setting system clock to 2008-10-06 04:22:17 UTC (1223266937) 
[    5.088224] ACPI: Processor [CPU] (supports 8 throttling states) 
[    9.120280] hub 1-0:1.0: 2 ports detected 
[   10.154015] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   10.154465] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   10.567610] PM: Starting manual resume from disk 
[   10.567621] PM: Resume from partition 8:5 
[   12.666097] kjournald starting.  Commit interval 5 seconds 
[   21.187337] udevd version 124 started 
[   26.820514] Linux agpgart interface v0.103 
[   27.212981] agpgart-intel 0000:00:00.0: Intel 440BX Chipset 
[   27.217766] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000 
[   28.460097] pccard: CardBus card inserted into slot 1 
[   28.460229] pci 0000:06:00.0: supports D1 
[   28.460234] pci 0000:06:00.0: supports D2 
[   28.460241] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot 
[   32.556727] parport_pc 00:0d: reported by Plug and Play ACPI 
[   32.556793] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE] 
[   32.991458] cs: IO port probe 0x100-0x3af: clean. 
[   32.992312] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7 
[   32.992686] cs: IO port probe 0x820-0x8ff: clean. 
[   32.993005] cs: IO port probe 0xc00-0xcf7: clean. 
[   32.993539] cs: IO port probe 0xa00-0xaff: clean. 
[   32.994533] cs: IO port probe 0x100-0x3af: clean. 
[   32.995329] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7 
[   32.995700] cs: IO port probe 0x820-0x8ff: clean. 
[   32.996070] cs: IO port probe 0xc00-0xcf7: clean. 
[   32.996601] cs: IO port probe 0xa00-0xaff: clean. 
[   33.500414] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them 
[   35.152573] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01 
[   35.217762] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.27-5-generic 
[   35.884713] gameport: CS46xx Gameport is pci0000:00:05.0/gameport0, speed 1704kHz 
[   37.563759] lp0: using parport0 (interrupt-driven). 
[   47.286106] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use) 
[   47.960304] ppdev: user-space parallel port driver 
[   87.494434] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   99.888081] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[   99.888104] wlan0: issue_cmd(cmd:0x0002) FAILED 
[   99.888746] wlan0: configure(type:0x1010) FAILED 
[  103.524089] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[  103.524112] wlan0: issue_cmd(cmd:0x0016) FAILED 
[  106.908104] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[  106.908128] wlan0: issue_cmd(cmd:0x0016) FAILED 
[  119.836066] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[  119.836090] wlan0: issue_cmd(cmd:0x0016) FAILED 
[  154.696069] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[  154.696093] wlan0: issue_cmd(cmd:0x0016) FAILED 
[  160.924118] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[  160.924144] wlan0: issue_cmd(cmd:0x0016) FAILED 
[  163.780079] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[  163.780104] wlan0: issue_cmd(cmd:0x0016) FAILED 
[  180.072116] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[  180.072149] wlan0: issue_cmd(cmd:0x0016) FAILED 
[  193.476114] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[  193.476138] wlan0: issue_cmd(cmd:0x0016) FAILED 
[  200.624095] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[  200.624118] wlan0: issue_cmd(cmd:0x0016) FAILED 
[  216.296076] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x2000 irq_status:0x2000 timeout:49ms cmd_status:1 (Success) 
[  216.296100] wlan0: issue_cmd(cmd:0x0016) FAILED 
[  225.488076] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[  225.488101] wlan0: issue_cmd(cmd:0x0016) FAILED 
[  225.680067] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success) 
[  225.680091] wlan0: issue_cmd(cmd:0x0016) FAILED 
fitz@fitz-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:04:76:60:6f:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:11 Base address:0x4400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:226 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:11300 (11.3 KB)  TX bytes:11300 (11.3 KB) 

fitz@fitz-laptop:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

irda0     Interface doesn't support scanning. 

wlan0     Interface doesn't support scanning : Resource temporarily unavailable 

pan0      Interface doesn't support scanning.

---

### Post by pytheas22 on 2008-10-06
dunbrokin,

It looks like your wireless interface is down.  What happens if you type:
```

sudo ifconfig wlan0 up
```

Your issue may or may not be the same as that of the original poster, but we'll try to solve it either way (I may ask you to start a new thread, though, if it turns out not to be the same problem, just so that things don't get convoluted).

---

### Post by kvk on 2008-10-06
Okay- here's my output. Thanks for being willing to look this over! The wireless interface, the Ralink RT2561/R61, has native support in Ibex (but not in Hardy), as evidenced by its original connection; I'm just not sure why it refuses to connect since the first time. Thanks again!!!

arctos@arctos:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: wmaster0
       version: 00
       serial: 00:1d:7e:9e:e9:b0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:1d:7d:d1:3d:5c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:00:70:9d:b2:ca
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
arctos@arctos:~$ lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation MCP73 Host Bridge [10de:07c1] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07cb] (rev a2)
00:01.0 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07cd] (rev a1)
00:01.1 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07ce] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07cf] (rev a1)
00:01.3 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07d0] (rev a1)
00:01.4 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07d1] (rev a1)
00:01.5 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07d2] (rev a1)
00:01.6 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07d3] (rev a1)
00:02.0 RAM memory [0500]: nVidia Corporation nForce 630i memory controller [10de:07d6] (rev a1)
00:03.0 ISA bridge [0601]: nVidia Corporation MCP73 LPC Bridge [10de:07d7] (rev a2)
00:03.1 SMBus [0c05]: nVidia Corporation MCP73 SMBus [10de:07d8] (rev a1)
00:03.2 RAM memory [0500]: nVidia Corporation MCP73 Memory Controller [10de:07d9] (rev a1)
00:03.4 RAM memory [0500]: nVidia Corporation MCP73 Memory Controller [10de:07c8] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation GeForce 7100/nForce 630i [10de:07fe] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation GeForce 7100/nForce 630i [10de:056a] (rev a1)
00:08.0 IDE interface [0101]: nVidia Corporation MCP73 IDE [10de:056c] (rev a1)
00:0a.0 PCI bridge [0604]: nVidia Corporation MCP73 PCI Express bridge [10de:056d] (rev a1)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP73 PCI Express bridge [10de:056e] (rev a1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP73 PCI Express bridge [10de:056f] (rev a1)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP73 PCI Express bridge [10de:056f] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation Device [10de:07f0] (rev a2)
00:0f.0 Ethernet controller [0200]: nVidia Corporation MCP73 Ethernet [10de:07dc] (rev a2)
00:10.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7100/nForce 630i [10de:07e1] (rev a2)
01:05.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
01:07.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
arctos@arctos:~$ dmesg | grep -e iwl -e wlan -e rt -e ath
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at e4000000 (gap: e2000000:1cc00000)
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.004000] virtual kernel memory layout:
[    0.244015] ...trying to set up timer as Virtual Wire IRQ...
[    0.376131] Booting paravirtualized kernel on bare hardware
[    0.390970] ACPI: (supports S0 S1 S4 S5)
[    0.404962] PCI: 0000:00:03.1 reg 10 io port: [c000, c03f]
[    0.404976] PCI: 0000:00:03.1 reg 20 io port: [1c00, 1c3f]
[    0.404982] PCI: 0000:00:03.1 reg 24 io port: [1c80, 1cbf]
[    0.405000] pci 0000:00:03.1: PME# supported from D3hot D3cold
[    0.405179] pci 0000:00:04.0: supports D1
[    0.405181] pci 0000:00:04.0: supports D2
[    0.405184] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.405246] pci 0000:00:04.1: supports D1
[    0.405248] pci 0000:00:04.1: supports D2
[    0.405250] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.405294] PCI: 0000:00:08.0 reg 20 io port: [f000, f00f]
[    0.405367] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.405402] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.405437] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.405462] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]
[    0.405467] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]
[    0.405472] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]
[    0.405477] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]
[    0.405481] PCI: 0000:00:0e.0 reg 20 io port: [dc00, dc0f]
[    0.405527] PCI: 0000:00:0f.0 reg 14 io port: [e000, e007]
[    0.405558] pci 0000:00:0f.0: supports D1
[    0.405560] pci 0000:00:0f.0: supports D2
[    0.405562] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.405769] pci 0000:01:07.0: supports D1
[    0.405771] pci 0000:01:07.0: supports D2
[    0.405774] pci 0000:01:07.0: PME# supported from D0 D1 D2 D3hot
[    0.405858] PCI: bridge 0000:00:0b.0 io port: [9000, 9fff]
[    0.405906] PCI: bridge 0000:00:0c.0 io port: [b000, bfff]
[    0.405953] PCI: bridge 0000:00:0d.0 io port: [a000, afff]
[    0.502702] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.524031] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.524035] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.524038] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.524042] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.524045] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.524049] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.524068] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.524072] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.524075] system 00:02: ioport range 0x295-0x314 has been reserved
[    0.524079] system 00:02: ioport range 0x290-0x294 has been reserved
[    0.524082] system 00:02: ioport range 0x880-0x88f has been reserved
[    0.559298] bus: 00 index 0 io port: [0, ffff]
[    0.559309] bus: 01 index 3 io port: [0, ffff]
[    0.559314] bus: 02 index 0 io port: [9000, 9fff]
[    0.559323] bus: 03 index 0 io port: [b000, bfff]
[    0.559332] bus: 04 index 0 io port: [a000, afff]
[    1.068516] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.068548] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.068578] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.068622] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.068701] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.068731] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.068756] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.068800] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.068877] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.068907] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.068932] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.068973] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.439653] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.441044] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.441154] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.441364] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.441393] rtc0: alarms up to one year, y3k, hpet irqs
[    1.441838] Using IPI No-Shortcut mode
[    1.442074] rtc_cmos 00:04: setting system clock to 2008-10-06 05:15:41 UTC (1223270141)
[    2.726144] hub 1-0:1.0: 10 ports detected
[    2.932322] ehci_hcd 0000:00:04.1: debug port 1
[    2.932325] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    2.944005] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.944081] hub 2-0:1.0: 10 ports detected
[    3.205954] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    3.207927] ata1: SATA max UDMA/133 abar m8192@0xe5100000 port 0xe5100100 irq 220
[    3.207929] ata2: SATA max UDMA/133 abar m8192@0xe5100000 port 0xe5100180 irq 220
[    3.207931] ata3: SATA max UDMA/133 abar m8192@0xe5100000 port 0xe5100200 irq 220
[    3.207933] ata4: SATA max UDMA/133 abar m8192@0xe5100000 port 0xe5100280 irq 220
[    5.322220] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.322304] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.369018] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.369092] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.369095]  sdb: unknown partition table
[    5.496792] ata6: port disabled. ignoring.
[    5.583806] PM: Starting manual resume from disk
[    5.583808] PM: Resume from partition 8:5
[    5.621540] kjournald starting.  Commit interval 5 seconds
[   11.985238] udevd version 124 started
[   13.371571] Linux agpgart interface v0.103
[   13.832750] rt61pci 0000:01:05.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   13.878074] Registered led device: rt61pci-phy0:radio
[   13.878087] Registered led device: rt61pci-phy0:assoc
[  113.243165] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  114.251773] ppdev: user-space parallel port driver
[  118.272643] Modules linked in: bridge stp bnep rfcomm l2cap bluetooth ppdev cpufreq_ondemand cpufreq_conservative cpufreq_stats freq_table cpufreq_powersave cpufreq_userspace pci_slot sbs sbshc container video output battery af_packet iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport arc4 ecb crypto_blkcipher rt61pci crc_itu_t rt2x00pci rt2x00lib rfkill led_class mac80211 nvidia(P) cfg80211 agpgart eeprom_93cx6 i2c_core shpchp pci_hotplug wmi button evdev ext3 jbd mbcache sr_mod cdrom sg sd_mod crc_t10dif usbhid hid pata_amd ahci ata_generic pata_acpi ohci1394 ohci_hcd ehci_hcd libata forcedeth ieee1394 scsi_mod usbcore dock thermal processor fan fbcon tileblit font bitblit softcursor uvesafb fuse
[  119.945262] firmware: requesting rt2561s.bin
[  134.349584] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  191.584240] wlan0: Trigger new scan to find an IBSS to join
[  194.316007] wlan0: Trigger new scan to find an IBSS to join
[  197.048006] wlan0: Trigger new scan to find an IBSS to join
[  199.780006] wlan0: Trigger new scan to find an IBSS to join
[  200.512520] wlan0: Creating new IBSS network, BSSID ee:91:31:d2:12:7f
[  201.777966] wlan0: disassociating by local choice (reason=3)
[  202.472003] wlan0: no IPv6 routers present
[  295.827066] USB Mass Storage support registered.
arctos@arctos:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:d1:3d:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120580 (120.5 KB)  TX bytes:120580 (120.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:7e:9e:e9:b0  
          inet6 addr: fe80::21d:7eff:fe9e:e9b0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2458 (2.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-7E-9E-E9-B0-39-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

arctos@arctos:~$ sudo iwlist scan
[sudo] password for arctos: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

---

### Post by dunbrokin on 2008-10-06
> **pytheas22 said:**
> dunbrokin,

It looks like your wireless interface is down.  What happens if you type:
```

sudo ifconfig wlan0 up
```

Your issue may or may not be the same as that of the original poster, but we'll try to solve it either way (I may ask you to start a new thread, though, if it turns out not to be the same problem, just so that things don't get convoluted).


Nothing happens I just get prompt....I can use a wire to the router and that works. Also, I have 2 PCs on my desk (both running 8.10) the second PC is connected wirelessly with no problem...in fact I am writing this message on that PC.

---

### Post by Peter09 on 2008-10-06
I know it may be silly but check that the Hardware Switch on your PC which turns your wireless device on/off is in the on position.

---

### Post by kvk on 2008-10-06
I'd love it if that were the case!! :)

But my PC doesn't have a switch like that, unfortunately.

---

### Post by dunbrokin on 2008-10-06
> **Peter09 said:**
> I know it may be silly but check that the Hardware Switch on your PC which turns your wireless device on/off is in the on position.


Nor does mine I am afraid...

---

### Post by pytheas22 on 2008-10-06
dunbrokin,

After you typed 'sudo ifconfig wlan0 up', since you didn't get any error messages, you should have been able to scan for networks.  Can you?  In other words, what is the output of:
```

sudo ifconfig wlan0 up
sudo iwlist scan
lshw -C Network
```

Also, you may want to start a new thread...even though your behavior is the same as that of the original poster's, you have totally different wireless drivers, and I suspect that the source of the problem for each of you is very different.  If you start a new thread, please let me know the URL and I'll reply there.

kvk,

I don't see anything that explains per se why you can't connect.  One thing to try is using wicd instead of Network Manager.  Another thing is to see if you can connect with encryption disabled on your router.

If neither of those helps, we can install drivers for your card which are older but should be more reliable (the [serialmonkey legacy drivers]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page")).  They used to be included in Ubuntu a while back, but got dropped I think with Gutsy because they've been replaced be "next-generation" drivers, which, while nice, still don't work as well as they should in some cases.

---

### Post by kvk on 2008-10-06
Hi Pytheas~

Thanks for looking all that over. I currently have no encryption set on the router. 

I didn't know wicd was included in Ibex! I tried to open it but I don't think it's there. Is it hidden somewhere?

kvk

---

### Post by dunbrokin on 2008-10-06
> **pytheas22 said:**
> dunbrokin,

After you typed 'sudo ifconfig wlan0 up', since you didn't get any error messages, you should have been able to scan for networks.  Can you?  In other words, what is the output of:
```

sudo ifconfig wlan0 up
sudo iwlist scan
lshw -C Network
```

Also, you may want to start a new thread...even though your behavior is the same as that of the original poster's, you have totally different wireless drivers, and I suspect that the source of the problem for each of you is very different.  If you start a new thread, please let me know the URL and I'll reply there.

kvk,

I don't see anything that explains per se why you can't connect.  One thing to try is using wicd instead of Network Manager.  Another thing is to see if you can connect with encryption disabled on your router.

If neither of those helps, we can install drivers for your card which are older but should be more reliable (the [serialmonkey legacy drivers]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page")).  They used to be included in Ubuntu a while back, but got dropped I think with Gutsy because they've been replaced be "next-generation" drivers, which, while nice, still don't work as well as they should in some cases.


I have moved my post to 

[http://ubuntuforums.org/showthread.php?t=939298](http://ubuntuforums.org/showthread.php?t=939298)

Thanks for your help.

---

### Post by pytheas22 on 2008-10-06
> Hi Pytheas~

Thanks for looking all that over. I currently have no encryption set on the router.

I didn't know wicd was included in Ibex! I tried to open it but I don't think it's there. Is it hidden somewhere?

kvk

You're right, wicd is not included in Intrepid.  I meant to provide a hyperlink to the wicd site, where you can find instructions for installing it, but forgot.  Anyway, go to wicd.sourceforge.net and you'll be able to install it (if they don't have instructions up for Ubuntu 8.10, just follow the ones for 8.04 and it should work fine).  Also, installing wicd will force you to uninstall Network Manager.  If you want NM back later, just type:
```

sudo apt-get install network-manager-gnome
```

Please let me know if you have better luck connecting in wicd.  If not, we can try the serialmonkey drivers.

---

### Post by dunbrokin on 2008-10-06
> **pytheas22 said:**
> You're right, wicd is not included in Intrepid.  I meant to provide a hyperlink to the wicd site, where you can find instructions for installing it, but forgot.  Anyway, go to wicd.sourceforge.net and you'll be able to install it (if they don't have instructions up for Ubuntu 8.10, just follow the ones for 8.04 and it should work fine).  Also, installing wicd will force you to uninstall Network Manager.  If you want NM back later, just type:
```

sudo apt-get install network-manager-gnome
```

Please let me know if you have better luck connecting in wicd.  If not, we can try the serialmonkey drivers.


I tried to follow the instructions to download wicd as you suggested but had no luck.....their instructions are a bit obscure.

---

### Post by kvk on 2008-10-06
Well, wicd didn't help either. Dang! I had the connection initially using NM, so I am assuming it must be a driver or some other software issue, as opposed to the wireless card itself being buried in the PC case.

---

### Post by kvk on 2008-10-06
OKay- I've downloaded RutilT and the most recent beta release of the R61 driver: rt61-1.1.0-b2

Is there somewhere in particular the driver would like to live? Or should I just extract these to somewhere  within etc/ ?

Thanks!!

---

### Post by pytheas22 on 2008-10-06
To install the rt61 driver from source, you will need to run a few commands.  First, you need to blacklist the drivers for your card that ship default with Ubuntu (since they don't seem to work):
```

sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
exit
```

Then cd into the directory where the rt61 source code is stored, and run these commands to compile and install it:
```

sudo apt-get install build-essential rutilt
tar -xzvf rt61*
cd rt61*
cd Module
make
sudo make install
```

That *should* work (although I typed this all from memory, so I may have missed something, and also I'm assuming that this will all work the same as in Hardy, but that's not guaranteed...) and you should be able to connect after a reboot.  **An important difference, however, is that you will not be able to connect using Network Manager or wicd**.  Instead, you have to use a program called Rutilt, which should be installed at System>Administration>Rutilt Wireless Manager.

If things still don't work after rebooting, please post the output of the following commands:
```

lshw -C Network
sudo iwlist scan
lsmod | grep rt
```

---

### Post by kvk on 2008-10-07
Well I'm TRYING to extract the driver but it keeps telling me I don't have permission to do that! Argh!! I modified the User/Groups profile so that I'm a member of 'root' but it still shuts me out. I also tried to create the root account, but when I tried to log in from the primary log-in screen, I was told "System Administrator is not allowed to login from this screen".

I'm sorry this is turning into such a pain- how do I work around this conundrum?

---

### Post by kvk on 2008-10-07
Well I'm TRYING to extract the driver but it keeps telling me I don't have permission to do that! Argh!! I modified the User/Groups profile so that I'm a member of 'root' but it still shuts me out. I also tried to create the root account, but when I tried to log in from the primary log-in screen, I was told "System Administrator is not allowed to login from this screen".

I'm sorry this is turning into such a pain- how do I work around this conundrum?

---

### Post by AngelX on 2008-10-07
If you want to try the Wicd you'll need to do it manually not like it says on the Wicd website...

Do the repository thing (don't forget the updating after adding the reference)
    deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras

And in a terminal add the key also
    ```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

then (in the terminal) do:
    ```
sudo apt-get install wicd
```

Wicd installed fine, and I tried it but with no luck... wireless still not working... will post in another thread. Hope the above helps someone.

---

### Post by ELD on 2008-10-07
I also have the same problem

My Post > [http://ubuntuforums.org/showthread.php?t=937244](http://ubuntuforums.org/showthread.php?t=937244)

Worked on first boot, updated and then wireless no workie, finds my unsecured network but hangs on connecting and then fails heh, not good.

---

### Post by pytheas22 on 2008-10-07
> Well I'm TRYING to extract the driver but it keeps telling me I don't have permission to do that! Argh!! I modified the User/Groups profile so that I'm a member of 'root' but it still shuts me out. I also tried to create the root account, but when I tried to log in from the primary log-in screen, I was told "System Administrator is not allowed to login from this screen".


I don't know why it doesn't want to let you extract the file, but if you want to just become root permanently, type:
```

sudo -s
```

Then you'll be root until you close the terminal or type 'exit'.  Try extracting the file that way and please let us know if it works.  I'm sorry this is not going as smoothly as desired, but I'm pretty sure that once you get the serialmonkey driver installed, things should work.

---

### Post by kvk on 2008-10-08
Sorry it's taken me so long to get to this!

Things went fine until the 'make' command run from within the Module directory:

root@arctos:/etc/rt61-1.1.0-b2/Module# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-5-generic'
  CC [M]  /etc/rt61-1.1.0-b2/Module/rtmp_main.o
/etc/rt61-1.1.0-b2/Module/rtmp_main.c: In function ‘RT61_probe’:
/etc/rt61-1.1.0-b2/Module/rtmp_main.c:222: error: implicit declaration of function ‘SET_MODULE_OWNER’
/etc/rt61-1.1.0-b2/Module/rtmp_main.c: In function ‘RT61_open’:
/etc/rt61-1.1.0-b2/Module/rtmp_main.c:405: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/etc/rt61-1.1.0-b2/Module/rtmp_main.c:405: error: (Each undeclared identifier is reported only once
/etc/rt61-1.1.0-b2/Module/rtmp_main.c:405: error: for each function it appears in.)
/etc/rt61-1.1.0-b2/Module/rtmp_main.c: In function ‘rt61_init_module’:
/etc/rt61-1.1.0-b2/Module/rtmp_main.c:1044: error: implicit declaration of function ‘pci_module_init’
make[2]: *** [/etc/rt61-1.1.0-b2/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/etc/rt61-1.1.0-b2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-5-generic'
rt61.ko failed to build!
make: *** [module] Error 1
root@arctos:/etc/rt61-1.1.0-b2/Module# 

Have I made an error in constructing RutilT? Is that a prerequesite, or only a run dependency?

Thanks so much! Progress is being made!

---

### Post by pytheas22 on 2008-10-08
I couldn't compile the driver either.  It looks like a bug with the source code.

The good news, however, is that I was able to compile the 'CVS hourly tarball' version of the driver (as opposed to the 'last beta release' that you used before), which you can download [here]("http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz").  Please transfer it to your computer, cd into the directory where it's stored, and run these commands (make sure that the broken source code and any files related to it are removed before trying to run these commands):
```

sudo apt-get install build-essential
tar -xzvf rt61*
cd rt61*/Module
make
sudo make install
```

Please let me know if you have better luck with this, and sorry it didn't work the first time.

---

### Post by kvk on 2008-10-09
Progress is being made! I removed the old driver, installed the new one along with the RutilT. It opens and I defined my wireless ESSID, and it connects without a hitch.

HOwever, it states that the signal strength is only 74%, when the router is sitting two feet away from the box, and it won't actually fetch pages. It shows the connection correctly, but doesn't actually go anywhere. I have to plug the wired connection back in to do that.

Running lshw -C network shows the connection, defines it as wlan0, and doesn't indicate that it is disabled. It's just rather...inert. :-p

---

### Post by kvk on 2008-10-09
Update- for some reason the wireless functioned for about 30 seconds after unplugging the wired network cable. It was faster than any connection I've ever seen, and it wasn't just fetching pages from the cache- it opened a new email page. Then it died and has remained dead ever since.

---

### Post by pytheas22 on 2008-10-09
Please try connecting again.  As soon as it crashes, open a terminal, run these commands and post the output:
```

dmesg | tail
host google.com
ping google.com
ping 209.85.171.99
ifconfig
```

---

### Post by kvk on 2008-10-10
The output below was given while the RutilT listed the following wireless stats:

RT61 Wireless(wlan0)
ESSID: mynetwork
Link quality: 76%
Signal level: -63 dBm
Noise level: -95 dBm
Tx rate: 54 Mbps

It may mean nothing, but the original output on the first page of this thread gives:

description: Wireless interface
product: RT2561/RT61 802.11g PCI
vendor: RaLink
physical id: 5
bus info: pci@0000:01:05.0
logical name: wmaster0
version: 00
serial: 00:1d:7e:9e:e9:b0
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg


Notice that the title of the wireless interface is given as "wmaster0", whereas the current connection
is named "wlan0".


arctos@arctos:~$ dmesg | tail
[  225.257030] type=1503 audit(1223616332.731:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6708/net/" pid=6708 profile="/usr/sbin/cupsd"
[  225.258003] type=1503 audit(1223616332.731:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6708 profile="/usr/sbin/cupsd"
[  225.258811] type=1503 audit(1223616332.731:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6708 profile="/usr/sbin/cupsd"
[  225.259630] type=1503 audit(1223616332.731:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6708 profile="/usr/sbin/cupsd"
[  225.260420] type=1503 audit(1223616332.735:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6708 profile="/usr/sbin/cupsd"
[  225.261219] type=1503 audit(1223616332.735:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6708 profile="/usr/sbin/cupsd"
[  225.262034] type=1503 audit(1223616332.735:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6708 profile="/usr/sbin/cupsd"
[  225.262831] type=1503 audit(1223616332.735:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6708 profile="/usr/sbin/cupsd"
[  225.263618] type=1503 audit(1223616332.735:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6708 profile="/usr/sbin/cupsd"
[  257.247618] eth0: link down.
arctos@arctos:~$ host google.com
;; connection timed out; no servers could be reached
arctos@arctos:~$ ping google.com
ping: unknown host google.com
arctos@arctos:~$ ping 209.85.171.99
From 192.168.2.4 icmp_seq=1 Destination Host Unreachable

NOTE: the above line was repeated in ordered but not always sequential increments;
I halted the output when it hit 1000 and figured you wouldn't want to waste the space with
posting all of them.

arctos@arctos:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:d1:3d:5c  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fed1:3d5c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150693 (150.6 KB)  TX bytes:18016 (18.0 KB)
          Interrupt:219 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:170068 (170.0 KB)  TX bytes:170068 (170.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:7e:9e:e9:b0  
          inet6 addr: fe80::21d:7eff:fe9e:e9b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:21 txqueuelen:1000 
          RX bytes:4358765 (4.3 MB)  TX bytes:3676 (3.6 KB)
          Interrupt:16 

arctos@arctos:~$ 


Thanks again for all your

---

### Post by pytheas22 on 2008-10-10
The difference in the interface names and things (wmaster0 vs. wlan0) is caused by using a different driver; that's nothing to worry about.

It's still not clear what exactly is wrong, however.  Could you please connect again, and right after it crashes, post the entire output of the command:
```

dmesg
```

It will be pretty long, but unfortunately I don't know where else to look.  I was hoping that the snippet of dmesg that you posted above would point to the problem, but it doesn't really provide any useful information.

---

### Post by kvk on 2008-10-10
I ran the update manager, and had to rebuild the RT61 driver afterwards before RutilT would function.

I ran 

dmesg

after removing the wired connection- the wireless didn't function at all, even though the utility indicated the connection was up and running.

How can I extract the entire output of 

dmesg

to include here? My terminal window will only retain so much, and then begins to clip things off. I've set the scroll limit to 4000 lines, but it still terminates at the same place. I do notice that in the last few lines of the output, it states:

[  592.764003] wlan0: no IPv6 routers present

However, I can't post the output because the forum filters indicate that I have 19 "images" included, meaning bits and pieces of the output code for smilies or whatever emoticon happens to fit. 

It's Friday and I'm sure that this, along with a bunch of other posts. are sending you for beer! 

I tried to weed out the smilies, but with little success.

Suggestions?

Thank you!!

---

### Post by pytheas22 on 2008-10-11
If you type:
```

dmesg > ~/Desktop/dmesg.txt
```

it will pipe the total output to a text file on your desktop called 'dmesg.txt'.  You can attach that file here as an attachment (I don't think they have any limits on that).  Please let me know if that works.

The 'no IPv6 routers present' stuff is normal, but generally dmesg is not longer than 4000 lines, so hopefully it's spamming some useful information that will help to solve your problem.

---

### Post by kvk on 2008-10-11
Thanks again for helping me track all this down!

I had the wireless up and running simultaneously with the wired connection, but when I terminated the wired, everything halted as usual, even though the wireless link indicated that it was still functional. I ran the terminal command and attached the .txt file from it. I had to separate it out into more than one file- the forum has a 19.5 KB limit on text file attachments.

Thanks!

---

### Post by pytheas22 on 2008-10-12
Thanks for all the information.

I hate to say it, though, but I don't really see anything that stands out as the source of the problem.  I also don't see where you connected with wireless in the first place, though--usually dmesg records a successful connection but I don't see it.  Are you positive that you were actually connected with the wireless and not the ethernet?  You could check the output of 'ifconfig' to be sure; you want to have an IP address on 'wlan0', not 'eth0'.

You could try going back to the drivers that ship default with Intrepid; maybe they've fixed by now whatever was wrong with them.  To switch back, you need to open up your blacklist:
```

sudo gedit /etc/modprobe.d/blacklist
```

and remove all lines that look similar to:
```

blacklist rt2x00
blacklist rt2x00lib
```

There should be five or six of those lines, and they should all be at the end of of the file.  Remove them, then save the file, reboot, and see if you have any better luck with the wireless.

Also, you may want to try fiddling more with the ethernet stuff.  For example, what happens if you unplug the cable from your router, but leave it plugged in to your computer.  Does the wireless connection still die?  What happens if you put the ethernet interface down before unplugging the cable:
```

sudo ifconfig eth0 down
```

Does the wireless stay alive then?

---

### Post by kvk on 2008-10-12
Hi Pytheas~

I'll try your suggestions and see what happens.

I neglected to mention, however, that I have NOT been able to generate a successful connection since the first time, which makes me wonder if I ever did. I test the wireless by bringing up the connection and then removing the ethernet cable from the computer. I'm no longer wired, the wireless shows activity, but no page fetching or anything else. That's why dmesg didn't show a successful connection, because there wasn't one.

Let me go through and try everything you posted and I'll get back to you on the results ASAP.

Thanks!!

---

### Post by pytheas22 on 2008-10-12
> I'm no longer wired, the wireless shows activity, but no page fetching or anything else. That's why dmesg didn't show a successful connection, because there wasn't one.

That's interesting that you say that the wireless shows activity.  I wonder if it's a simple DNS issue.  What is the output of these commands when the wireless is showing activity:
```

ifconfig
cat /etc/resolv.conf
host google.com
ping -c 5 google.com
ping -c 5 64.233.187.99
```

Also please provide any other information you think would be pertinent after reviewing the thread.

---

### Post by kvk on 2008-10-13
Thanks for the new directions- I'll haul the box back upstairs where the modem is and try to connect again and I'll post the output.

The only new data I have:

Yesterday I started from scratch: wiped the drive, loaded Heron, and then upgraded to Ibex. The terminal returned an error with loading the Network Manager applet, so I reloaded it from Synaptic. It detected the wireless network without difficulty, I removed the wired connection, and it performed flawlessly. I kept the computer where it was (upstairs by the modem, router, and only phone jack in the house), rebooted with no wired connection, and again it run the wireless with no issues at all.

THEN- I moved the box downstairs where it is supposed to live. It refused to detect or connect. Through a harrowing experiment, I got the computer and router to within ten feet of each other, separated by a wall- still no connection. I can manually instruct it to connect, but it returns a disconnect as soon as it seems to reach an understanding with the router.

Can this simply be an issue of having the wireless card buried too deeply in the box? Does that conflict with connection over any decent distance? (Including, apparently, even just ten feet).

It also has a Penryn motherboard, but given the connection yesterday, that doesn't seem to be an issue.

It is an Antec cube case.

There is a BIOS error returned on start-up having to do with a timer- I'll get that written down and post it as well.

Give me a few hours to play Dad and I'll haul everything back upstairs and run the commands you posted.

Thanks again! I have an entire recording studio depending on getting this thing up and running. :-p

Either that or buy a 100-foot Ethernet cable and a lot of u-tacks!

---

### Post by pytheas22 on 2008-10-13
Yes, would be very interested to see if you can connect again with the computer and router back in the locations where they were when you could first connect.

Unless something weird is going on, though, this should not be an issue of your wireless card being 'buried' inside your computer--it should definitely work if the router is only ten feet away.

---

### Post by kvk on 2008-10-14
Well, I moved it back upstairs, plugged in it and booted up- it detected the wireless signal no problem- the results and this post are from that wireless signal. No wired connection was established.

Being right next to the router, it still shows a signal strength anywhere from 68% - 87%. Does that seem odd? Should it not be 100%? And the fact that it is less indicating some lack of connection capacity on the part of the wireless card? 


arctos@arctos:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:d1:3d:5c  
          inet6 addr: fe80::21d:7dff:fed1:3d5c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8183 (8.1 KB)  TX bytes:6494 (6.4 KB)
          Interrupt:219 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:7e:9e:e9:b0  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7eff:fe9e:e9b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1401988 (1.4 MB)  TX bytes:227518 (227.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-7E-9E-E9-B0-39-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

arctos@arctos:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain NOAA1
search NOAA1
nameserver 192.168.2.1
arctos@arctos:~$ host google.com
google.com has address 64.233.187.99
google.com has address 72.14.207.99
google.com has address 209.85.171.99
google.com mail is handled by 10 smtp3.google.com.
google.com mail is handled by 10 smtp4.google.com.
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 smtp2.google.com.
arctos@arctos:~$ ping -c 5 google.com
PING google.com (209.85.171.99) 56(84) bytes of data.
64 bytes from google.com (209.85.171.99): icmp_seq=1 ttl=244 time=61.0 ms
64 bytes from google.com (209.85.171.99): icmp_seq=2 ttl=244 time=78.0 ms
64 bytes from google.com (209.85.171.99): icmp_seq=3 ttl=244 time=64.0 ms
64 bytes from google.com (209.85.171.99): icmp_seq=4 ttl=244 time=70.1 ms
64 bytes from google.com (209.85.171.99): icmp_seq=5 ttl=244 time=118 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4018ms
rtt min/avg/max/mdev = 61.037/78.392/118.711/20.983 ms
arctos@arctos:~$ ping -c 5 64.233.187.99
PING 64.233.187.99 (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=245 time=131 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=245 time=132 ms
64 bytes from 64.233.187.99: icmp_seq=3 ttl=245 time=132 ms
64 bytes from 64.233.187.99: icmp_seq=4 ttl=245 time=134 ms
64 bytes from 64.233.187.99: icmp_seq=5 ttl=245 time=132 ms

--- 64.233.187.99 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4012ms
rtt min/avg/max/mdev = 131.720/132.704/134.871/1.190 ms
arctos@arctos:~$

---

### Post by pytheas22 on 2008-10-14
Very interesting...I guess it was just a driver issue all along.

We've already tried switching to the serialmonkey drivers, without luck.  The next best thing I can think of is to give ndiswrapper a try, which will let you drive the card using Windows drivers.  To use ndiswrapper, you will need to find the .inf and .sys files associated with your wireless card.  You can download the Windows driver from [here]("http://www.ralinktech.com.tw/data/drivers/IS_AP_STA_6x_D-1.2.3.0_VA-2.1.0.0_2500_D-3.2.0.0_VA-3.2.0.0_RU-2.0.4.0_VA-2.0.4.0_AU-1.2.1.0_VA-1.0.4.0_101707_0.1.0.29.exe"), but unfortunately, I'm not having any luck breaking it open to get at the necessary files--I even installed it on my Windows virtual machine, but I can't figure out where it put the relevant files, which usually are in windows\system32 but don't seem to be.

If you have drivers for this card on a CD, or have installed this card on a Windows system somewhere, you should be able to get at the necessary files.  Please let me know if you think you can locate them; if not, we can try harder to break that .exe open.

---

### Post by kvk on 2008-10-14
I'll get right on it, but what in the output makes you say it's a driver issue? If it's a driver issue, how is it connecting right now?

---

### Post by pytheas22 on 2008-10-14
Sorry, should have explained better (was trying to get to bed), but I think it's a driver issue because basically it seems to simply come down to signal strength: it works fine when your computer is right next to router, but not at normal distances, even at only ten feet (please correct me if that understanding is wrong).  So a different driver should give you a better signal strength.  The serialmonkey driver didn't seem to work for some weird reason, but under ndiswrapper you should get the same signal that you do in Windows (since it uses the same driver).

Please let me know if you can figure out where the .inf and .sys files that correspond to your wireless driver are.  They're probably (but not necessarily) named rt61.inf and rt61.sys, or something close to that.  The best way to find them is just to search your Windows system for all files with .inf in their name.

---

### Post by kvk on 2008-10-19
Well, I wasn't able to dissect the .exe file for the Windows driver either. Since time was becoming of the essence, I ran a 100ft Ethernet cable along the ceiling and down the stairs to the box, so I can at least run it as such while I try to figure out everything else. 

I really appreciate your help on all of this- I'll keep scratching away at it over time.

Thank you!!

---

### Post by pytheas22 on 2008-10-19
Well, sorry to hear that it came down to running a cable that far, but I'm glad you at least have an Internet connection now!

If you do get time to figure out where the relevant .inf and .sys files are hiding on your Windows system, let me know.

---

