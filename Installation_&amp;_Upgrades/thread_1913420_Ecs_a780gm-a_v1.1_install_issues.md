---
title: "Ecs a780gm-a v1.1 install issues"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by CSharpe67 on 2012-01-22
HI All,

I finally have been given permission to use my wife computer into a dual boot system of Mythbuntu 11.04 and WIn XP pro.  It's had Win XP Pro since Nov 2009 and has worked great.  So I had an extra hard drive and was attempting to install Mythbuntu.  The LiveCD says the ethernet does not work, yet I think the driver is loaded.

The specs from Newegg when I bought the motherboard were:

[LIST]
[*]1 x ECS BLACK SERIES A780GM-A AM2+/AM2 AMD 780G HDMI ATX AMD Motherboard
[*]1 x AMD Athlon II X2 245 Regor 2.9GHz Socket AM3 65W Dual-Core Desktop Processor ADX245OCGQBOX
[*]1 x G.SKILL 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model F2-6400CL5D-4GBPQ
[/LIST]
Early this year I bought a Zotac VGA card for dual outputs so I can have TV and a monitor in WinXP.  The LiveCD boots up on both, the install only shows one.



[LIST]
[*]1 x ZOTAC ZT-84MEG5M-HSL GeForce 8400 GS 256MB 64-bit DDR2 PCI Express 2.0 x16 HDCP Ready Low Profile Ready Video Card
[/LIST]


I am comfortable using terminal.  I have tried the following things.

sudo ifconfig: 

for output see attached below.

sudo ipconfig
ipconfig: command not found

I can play videos with sound through VLC.

Any other suggestion would be greatly appreciated.

---

### Post by CSharpe67 on 2012-01-22
I downloaded ubuntu 11.04 and ran the system Testing.

What does 
[B]ERROR:root:could not find def gateway info in /proc
ERROR:root:could not find default gateway by running route[/B]

Some more info after google for answer.  Other request were for the following information:

[B]sudo lspci 
[/B]

 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge  
 00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)  
 00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)  
 00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]  
 00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller  
 00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller  
 00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller  
 00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller  
 00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller  
 00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller  
 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)  
 00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller  
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)  
 00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller  
 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge  
 00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control  
 00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control  
 01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)  
 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)  
 03:05.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01) 
 03:06.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)  
 03:06.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)  
 03:06.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)  
 





**ifconfig ** 
 eth0      Link encap:Ethernet  HWaddr 00:25:11:43:26:af   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:42  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:316 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:316 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:24528 (24.5 KB)  TX bytes:24528 (24.5 KB)  
 





 **sudo lshw -C network ** 
   *-network                
        description: Ethernet interface  
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 02  
        serial: 00:25:11:43:26:af  
        size: 10Mbit/s  
        capacity: 1Gbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s  
        resources: irq:42 ioport:d800(size=256) memory:feaff000-feafffff memory:f8ff0000-f8ffffff memory:feac0000-feadffff  
 ubuntu@ubuntu:~$

---

