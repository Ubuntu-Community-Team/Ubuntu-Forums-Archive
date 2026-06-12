---
title: "Kernel update breaks ethernet interface"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by MarkusRTK on 2008-06-24
Hi -- just updated my kernel from 2.6.22-14-generic to 2.6.22-15-generic (on Gutsy), and when I boot to the new kernel my ethernet device (eth0) is no longer recognized. Ifconfig eth0 just shows an error while getting interface flags: no such device. Wireless (and the loopback interface) still exist and work fine, it's just ethernet.

When I boot to the older kernel, ethernet works fine, so it's not a big deal. But I'm curious if other people are having the same problem / if there's something I can do about it. Any thoughts would be appreciated, thanks.

---

### Post by MarkusRTK on 2008-06-24
Additional info -- I tried sudo lshw -C network, which I saw suggested in another post somewhere. This result seems indicative:

```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:bf:b4:ac:d0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () ip=192.168.1.104 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
```

I'm assuming the "UNCLAIMED" next to my ethernet controller is part of the problem. What does that mean / how do I fix it?

---

### Post by iaculallad on 2008-06-24
What does the command ifconfig -a displays?

```
ifconfig -a
```

Include also the result of:

```
lspci -nn
```

---

### Post by MarkusRTK on 2008-06-24
Ifconfig shows just what you'd expect, no mention of my ethernet interface (eth0):

```
markus@markus-laptop:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:1C:BF:B4:AC:D0  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:434 errors:16 dropped:1425 overruns:0 frame:0
          TX packets:393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7257789 (6.9 MB)  TX bytes:1515410 (1.4 MB)
          Interrupt:17 Base address:0x2000 Memory:fe7ff000-fe7fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16608 (16.2 KB)  TX bytes:16608 (16.2 KB)
```

If I try to ifconfig eth0 up, I just get:

```
markus@markus-laptop:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
```

lspci -nn returns:

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
02:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
```

---

### Post by iaculallad on 2008-06-24
The quoted message below must be your Eth0 interface (taken from lspci -nn) and it seems that it can't be recognize by Gutsy.

> 09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)

Try to follow this link from [bugs.launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135316") if it could help resolve your case.

---

### Post by MarkusRTK on 2008-06-24
Well -- it *is* recognized by Gutsy and completely functional when I use the older kernel (2.6.22-14), just not the newer one (2.6.22-15) which I downloaded yesterday. So something changed in that upgrade specifically.

Either way, that bug at Launchpad seems different (they couldn't even get a PCI ID, which I can)... idk.

---

