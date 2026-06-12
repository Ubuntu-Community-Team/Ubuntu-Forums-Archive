---
title: "Kubuntu 12.04 Lan Connections not functioning"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by Billyj82 on 2012-08-22
Hello this is my first time posting on here.  I have been an Ubuntu user for years and decided to give Kubuntu a try. Everything went fine but I can not get the ethernet working. When I open the networking center it says my driver is forcedeth, but connection is unavailable.  If I plug the LAN connection into my laptop it works fine.  I remember I had the same problem with Ubuntu a couple years ago but can not remember how it was fixed.  I believe I had to reinstall or update the forcedeth drivers.  My ethernet ports are directly on the motherboard (ASUS M2N-SLI Deluxe AM2 NVIDIA nForce 570). Here are some items I pulled for info:

> root@bill-server:/home/bill# lspci
00:00.0 RAM memory: NVIDIA Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a1)
00:02.1 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: NVIDIA Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: NVIDIA Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: NVIDIA Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
06:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
06:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
07:00.0 VGA compatible controller: NVIDIA Corporation G80 [GeForce 8800 GTS] (rev a2)

root@bill-server:/home/bill# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:c9:6d:fe  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:1b:fc:c9:7c:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18464 (18.4 KB)  TX bytes:18464 (18.4 KB)


---

### Post by oldfred on 2012-08-24
I have not had Ethernet issues for ages. 

You are showing two? eth0 & eth1. Do you have two Ethernet connections? Or perhaps a conflict?

---

### Post by SeijiSensei on 2012-08-24
I don't even see an entry for an Ethernet controller in that list of hardware, yet ifconfig reports your having two adapters?

What if you try to configure the adapter manually?  Assuming for the moment that your router has the address 192.168.1.1, then you can try:

```

sudo ifconfig eth0 192.168.1.200 netmask 255.255.255.0 broadcast 192.168.1.255
sudo ip route add default via 192.168.1.1

```

What happens when you try that?

Do you also have a wifi adapter in this machine?  If so, try disabling that, and see if the machine will connect over Ethernet.

---

### Post by Billyj82 on 2012-08-24
@oldfred my motherboard has 2 ethernet adapters and I have tried both.  No matter which one the cable is plugged into the desktop says cable unplugged.

@SeijiSensei I tried setting a static IP and no luck, and no wifi adapter

---

