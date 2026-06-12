---
title: "[ubuntu] Atheros AR242x 802.11 in Ubuntu 9.04 Jaunty not working"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hosoka on 2009-04-07
No Wifi access on Jaunty with my Compaq Presario CQ50-100ED



I've done some commands and getting these outcomes from the Terminal. Hope this will helps out:

          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

pan0 no wireless extensions.

hosoka@hosoka-laptop:~$ ping -c 4 google.com
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=243 time=132 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=2 ttl=243 time=131 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=243 time=132 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=4 ttl=243 time=133 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 131.109/132.352/133.753/1.006 ms
hosoka@hosoka-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1d:72:65:dc:d8
          inet addr:192.168.1.6 Bcast:192.168.1.255 Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe65:dcd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:670539 (670.5 KB) TX bytes:155532 (155.5 KB)
          Interrupt:253 Base address:0x6000

lo Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)

wlan0 Link encap:Ethernet HWaddr 00:1f:e2:b0:48:2e
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0 Link encap:UNSPEC HWaddr 00-1F-E2-B0-48-2E-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

hosoka@hosoka-laptop:~$ netstat -r
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
192.168.1.0 * 255.255.255.0 U 0 0 0 eth0
link-local * 255.255.0.0 U 0 0 0 eth0
default 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
hosoka@hosoka-laptop:~$ sudo lshw -C network
[sudo] password for hosoka:
  *-network
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:65:dc:d8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.6 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:e2:b0:48:2e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:cd:13:6b:16:84
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200M G (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
hosoka@hosoka-laptop:~$ ls
Desktop Documents Examples Music Pictures Public Templates Videos
hosoka@hosoka-laptop:~$ clear

hosoka@hosoka-laptop:~$ sudo aptitude install hwinfo
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  hwinfo libhd15{a}
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 718kB of archives. After unpacking 1978kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe libhd15 15.3-1ubuntu1 [673kB]
Get:2 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe hwinfo 15.3-1ubuntu1 [44.9kB]
Fetched 718kB in 1s (489kB/s)
Selecting previously deselected package libhd15.
(Reading database ... 107998 files and directories currently installed.)
Unpacking libhd15 (from .../libhd15_15.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package hwinfo.
Unpacking hwinfo (from .../hwinfo_15.3-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libhd15 (15.3-1ubuntu1) ...

Setting up hwinfo (15.3-1ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

hosoka@hosoka-laptop:~$ clear

hosoka@hosoka-laptop:~$ hwinfo --netcard
07: PCI 700.0: 0282 WLAN controller
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_168c_1c
  Unique ID: y9sn.9AnOduZyIOF
  Parent ID: MZfG.K0fHNnB0W84
  SysFS ID: /devices/pci0000:00/0000:00:14.0/0000:07:00.0
  SysFS BusID: 0000:07:00.0
  Hardware Class: network
  Model: "Atheros AR242x 802.11abg Wireless PCI Express Adapter"
  Vendor: pci 0x168c "Atheros Communications, Inc."
  Device: pci 0x001c "AR242x 802.11abg Wireless PCI Express Adapter"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x137b
  Revision: 0x01
  Driver: "ath5k_pci"
  Driver Modules: "ath5k"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xc2000000-0xc200ffff (rw,non-prefetchable)
  IRQ: 23 (154 events)
  HW Address: 00:1f:e2:b0:48:2e
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v0000168Cd0000001Csv0000103Csd0000137Bbc02sc00i00"
  Driver Info #0:
    Driver Status: ath5k is active
    Driver Activation Cmd: "modprobe ath5k"
  Driver Info #1:
    Driver Status: ath_pci is not active
    Driver Activation Cmd: "modprobe ath_pci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

16: PCI 0a.0: 0200 Ethernet controller
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_10de_760
  Unique ID: rBUF.HOUiokKC0A4
  SysFS ID: /devices/pci0000:00/0000:00:0a.0
  SysFS BusID: 0000:00:0a.0
  Hardware Class: network
  Model: "nVidia Ethernet controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0760
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x360a
  Revision: 0xa2
  Driver: "forcedeth"
  Driver Modules: "forcedeth"
  Device File: eth0
  Memory Range: 0xc0009000-0xc0009fff (rw,non-prefetchable)
  I/O Ports: 0x30f8-0x30ff (rw)
  Memory Range: 0xc0007c00-0xc0007cff (rw,non-prefetchable)
  Memory Range: 0xc0007800-0xc000780f (rw,non-prefetchable)
  IRQ: 2301 (65538 events)
  HW Address: 00:1d:72:65:dc:d8
  Link detected: yes
  Module Alias: "pci:v000010DEd00000760sv0000103Csd0000360Abc02sc00i00"
  Driver Info #0:
    Driver Status: forcedeth is active
    Driver Activation Cmd: "modprobe forcedeth"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$ sudo iwlist scanning
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wmaster0 Interface doesn't support scanning.

wlan0 No scan results

pan0 Interface doesn't support scanning.

hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:65:dc:d8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.6 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:e2:b0:48:2e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:cd:13:6b:16:84
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation Device [10de:075e] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] IDE [10de:0759] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) [10de:0ad0] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP78S [GeForce 8200] Ethernet [10de:0760] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0569] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
02:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8200M G [10de:0845] (rev a2)
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$ lsusb
Bus 002 Device 002: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$ uname -a
Linux hosoka-laptop 2.6.28-11-generic #40-Ubuntu SMP Fri Apr 3 17:39:51 UTC 2009 i686 GNU/Linux
hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$ dmesg |grep ound
[ 0.000000] found SMP MP-table at [c00f7ff0] 000f7ff0
[ 0.512747] ACPI: No dock devices found.
[ 0.551712] pnp: PnP ACPI: found 12 devices
[ 1.186060] pcieport-driver 0000:00:14.0: found MSI capability
[ 1.709191] isapnp: No Plug & Play device found
[ 3.356633] hub 1-0:1.0: USB hub found
[ 3.368596] hub 2-0:1.0: USB hub found
[ 3.426394] hub 3-0:1.0: USB hub found
[ 3.482603] hub 4-0:1.0: USB hub found
[ 3.516824] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 3.518228] powernow-k8: Found 1 AMD Sempron(tm) SI-40 processors (1 cpu cores) (version 2.20.00)
[ 3.518715] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 4.092394] usb-storage: device found at 2
[ 11.190467] uvcvideo: Found UVC 1.00 device CNF7047 (04f2:b091)
[ 12.040846] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[ 12.990050] lp: driver loaded but no devices found
hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$ dmesg |grep witch
[ 0.016786] SMP alternatives: switching to UP code
[ 0.466423] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 0.548020] Switched to high resolution mode on CPU 0
[ 1.283695] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[ 1.285607] ACPI: Lid Switch [LID0]
hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:""
          Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry min limit:7 RTS thr:off Fragment thr=2352 B
          Power Management:off
          Link Quality:0 Signal level:0 Noise level:0
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

pan0 no wireless extensions.

hosoka@hosoka-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 [Auto eth0] ----------------------------------------------------
  Type: Wired
  Driver: forcedeth
  State: connected
  Default: yes
  HW Address: 00:1D:72:65:DC:D8

  Capabilities:
    Carrier Detect: yes
    Speed: 100 Mb/s

  Wired Properties
    Carrier: on

  IPv4 Settings:
    Address: 192.168.1.6
    Prefix: 24 (255.255.255.0)
    Gateway: 192.168.1.1

    DNS: 192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type: 802.11 WiFi
  Driver: ath5k_pci
  State: disconnected
  Default: no
  HW Address: 00:1F:E2:B0:48:2E

  Capabilities:

  Wireless Properties
    WEP Encryption: yes
    WPA Encryption: yes
    WPA2 Encryption: yes

  Wireless Access Points

hosoka@hosoka-laptop:~$ ping -c 4 google.com
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=243 time=133 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=2 ttl=243 time=132 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=243 time=132 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=4 ttl=243 time=132 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 132.253/132.655/133.444/0.595 ms
hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1d:72:65:dc:d8
          inet addr:192.168.1.6 Bcast:192.168.1.255 Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe65:dcd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:1309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1424082 (1.4 MB) TX bytes:177050 (177.0 KB)
          Interrupt:253 Base address:0x6000

lo Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)

wlan0 Link encap:Ethernet HWaddr 00:1f:e2:b0:48:2e
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0 Link encap:UNSPEC HWaddr 00-1F-E2-B0-48-2E-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$ netstat -r
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
192.168.1.0 * 255.255.255.0 U 0 0 0 eth0
link-local * 255.255.0.0 U 0 0 0 eth0
default 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
hosoka@hosoka-laptop:~$
hosoka@hosoka-laptop:~$

---

### Post by stchman on 2009-04-07
You will need a wire, but you can enable the following package:

```
sudo apt-get install linux-backports-modules-jaunty
```

That is what I used to get the card to work.

---

### Post by cariboo on 2009-04-08
@hosoka

Could you please use the [noparse]```

```[/noparse] tags when posting command outputs, it makes it much easier for use to read.

I've moved this thread to where it may get more response 

Jim

---

