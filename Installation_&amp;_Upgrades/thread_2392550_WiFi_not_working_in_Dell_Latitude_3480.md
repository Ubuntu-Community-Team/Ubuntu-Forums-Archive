---
title: "WiFi not working in Dell Latitude 3480"
date: 2018-05-22
forum: Installation &amp; Upgrades
---

### Post by nichurocks on 2018-05-22
hello All,

i am very new to Linux, in fact its the first time i am working on the same. i got a new lap DELL Latitude 3480. i got it with Windows and Linux 14.04 LTS installed. Windows 10 works perfectly but Linux is causing a lot of issues. the drivers were not properly installed and i was referring to variable posts available in the forum to find my way around. i was able to fix USB and Audio issues but unfortunately am in dire need of help with the WiFi drivers. my WiFi doesn't work... it doesn't even show the available wifi devices. With the help from Forum i ran the following commands and here are the results:

```
lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Dell Device [1028:07b7]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:0050]
```


```
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
```

```
lspci -vvnn | grep -A 9 Network
03:00.0 Network controller [0280]: Intel Corporation Wireless 8265 / 8275 [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:0050]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at f1000000 (64-bit, non-prefetchable) [disabled] [size=8K]
    Capabilities: <access denied>
```

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 58:8a:5a:0b:35:da
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.8.85 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:127 ioport:e000(size=256) memory:f1104000-f1104fff memory:f1100000-f1103fff
  *-network UNCLAIMED
       description: Network controller
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:f1000000-f1001fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

What i understand from this is that my driver is not installed otherwise it will not come as unclaimed network but whatever i do i am not able to find a way around it. From Windows i understand that the WiFi chipset is Intel(R) Dual band wireless - AC 8265. It works perfectly in Windows.

highly appreciate your support in advance

regards
nishant

---

