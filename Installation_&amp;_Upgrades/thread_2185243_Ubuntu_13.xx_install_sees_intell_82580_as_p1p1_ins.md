---
title: "Ubuntu 13.xx install sees intell 82580 as p1p1 instead of eth0"
date: 2013-11-01
forum: Installation &amp; Upgrades
---

### Post by eclay on 2013-11-01
Hello,

I've run into a strange issue where when I install ubuntu 13.xx it detects/names the NICs as p1p# instead of eth#.  This is making it difficult to perform automated (preseed) installs of multiple systems.  The system I'm running into this issue has a 82580 intel NICs in it.  When I install Debian 7.1 on the same systems the NICs are found as eth0 and eth1.  

Anyone seeing this same issue with this NIC model or have a suggestion on how to get the nics to be seen as eth0 and eth1?

Attached are screen shots of Debian/Ubuntu displaying the select interface to perform install screen.

~# lspci|grep -i eth
01:00.0 Ethernet controller: Intel Corporation 82580 Gigabit Network Connection (rev 01)
01:00.1 Ethernet controller: Intel Corporation 82580 Gigabit Network Connection (rev 01) # lspci -vs 01:00.0
01:00.0 Ethernet controller: Intel Corporation 82580 Gigabit Network Connection (rev 01)
        Subsystem: Super Micro Computer Inc Device 0000
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f7980000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at e020 [size=32]
        Memory at f7a04000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
        Capabilities: [70] MSI-X: Enable+ Count=10 Masked-
        Capabilities: [a0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Device Serial Number 00-25-90-ff-ff-6c-68-cc
        Capabilities: [1a0] Transaction Processing Hints
        Capabilities: [1c0] Latency Tolerance Reporting
        Kernel driver in use: igb
 # ifconfig |grep p1p
p1p1      Link encap:Ethernet  HWaddr 00:25:90:6c:68:cc
p1p2      Link encap:Ethernet  HWaddr 00:25:90:6c:68:cd
 System Information
        Manufacturer: Supermicro
        Product Name: X9SCD
        Version: 0123456789

---

### Post by eclay on 2013-11-01
forgot to attach screenshots.

---

