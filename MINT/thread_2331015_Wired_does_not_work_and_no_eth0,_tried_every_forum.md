---
title: "Wired does not work and no eth0, tried every forum!"
date: 2016-07-17
forum: MINT
---

### Post by Christophe_Duchesn on 2016-07-17
hey guys

Im on linux mint 18.

When a plug my ethernet cable in my computer (hp-pavilion-notebook), its showing " connecting ..." but never actually connect...I have tried every command line in every forums about this. I even tried to reinstall Mint all over again but the wired still doesn't work!!! 

somme command line that may help you:

$ifconfig

```
eno1      Link encap:Ethernet  HWaddr 3c:a8:2a:b4:5e:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:13158 (13.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:756645 (756.6 KB)  TX bytes:756645 (756.6 KB)

wlo1      Link encap:Ethernet  HWaddr d8:5d:e2:99:95:1d  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1a8f:6c92:34ec:5a63/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68491 errors:0 dropped:0 overruns:0 frame:24594
          TX packets:53870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:65722856 (65.7 MB)  TX bytes:7528545 (7.5 MB)
          Interrupt:18 

```

$ifup eth0

```
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Cannot find device "eth0"
Error getting hardware address for "eth0": No such device

If you think you have received this message due to a bug rather
than a configuration issue please read the section on submitting
bugs on either our web page at www.isc.org or in the README file
before submitting a bug.  These pages explain the proper
process and the information we find helpful for debugging..

exiting.
Failed to bring up eth0.
```

$lshw -class network
```
  *-network               
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlo1
       version: 01
       serial: d8:5d:e2:99:95:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.0.104 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:c6100000-c6107fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eno1
       version: 0a
       serial: 3c:a8:2a:b4:5e:38
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8107e-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:49 ioport:4000(size=256) memory:c6004000-c6004fff memory:c6000000-c6003fff

```

Thank you for your time and help, if you want more command line just ask :)

---

### Post by howefield on 2016-07-17
Thread moved to the "*MINT*" forum.

---

### Post by Christophe_Duchesn on 2016-07-17
also:

$cat /etc/network/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

I added myself the 3 last line, saw it in another thread!

---

### Post by jeremy31 on 2016-07-17
You may want to try r8168-dkms package as some ethernet devices using r8169 work better using r8168

---

### Post by Christophe_Duchesn on 2016-07-17
I installed it, do I have to purge r8169?

---

### Post by jeremy31 on 2016-07-17
Most you can do is blacklist it if it interferes, post ```
lspci -nnk | grep -iA2 net
``` as I want to look into the source code for it a bit

---

### Post by SeijiSensei on 2016-07-17
Looks to me like this version of Ubuntu changed the name of the Ethernet interface from eth0 to eno1.  

```
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       **logical name: eno1**

```
(Not only has the name changed but the decades-old numbering convention seems to have changed as well.)  Try using
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eno1
iface eno1 inet dhcp

```

---

### Post by gordintoronto on 2016-07-17
+! SeijiSensei!

In Mint 18, my Ethernet is enp3s0, and my wireless is wlp4s7

---

