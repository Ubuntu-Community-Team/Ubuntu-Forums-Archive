---
title: "nvidia ethernet driver problem"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by rvega022 on 2011-03-15
I just installed ubuntu 10.10 64 bit, when using the "run ubuntu from CD" everything ran great. But once I installed the OS, my ethernet port no long is working. I ran ubuntu again from the CD and my ethernet port is working.

What could be happening here?

do I have to activate a driver?
:confused:

---

### Post by plucky on 2011-03-15
> **rvega022 said:**
> I just installed ubuntu 10.10 64 bit, when using the "run ubuntu from CD" everything ran great. But once I installed the OS, my ethernet port no long is working. I ran ubuntu again from the CD and my ethernet port is working.

What could be happening here?

do I have to activate a driver?
:confused:

Left click on the Network icon and select **Edit Connections**

In the window that opens select **Wired** and Add a connection.Then make sure "Auto DHCP" is ticked in the window.

If that doesn't work,post output from a terminal for ```
lspci
ifconfig
```


Good Luck

---

### Post by rvega022 on 2011-03-15
Plucky,

I did the lspci and ifconfig and got the following:
  	 	 	 	p { margin-bottom: 0.08in; }  homeone@homeone-LX6810-01:~$ lspci  
 00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)  
 00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)  
 00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)  
 00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)  
 00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)  
 00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)  
 00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)  
 00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)  
 00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)  
 00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)  
 00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)  
 00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)  
 00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)  
 00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)  
 00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)  
 00:0b.0 RAID bus controller: nVidia Corporation MCP79 RAID Controller (rev b1)  
 00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)  
 00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)  
 00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)  
 00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)  
 00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)  
 01:07.0 Communication controller: Agere Systems Lucent V.92 Data/Fax Modem  
 02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce GT 120] (rev a1)  
 04:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 0f)  
 05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller  
 homeone@homeone-LX6810-01:~$  
 

 homeone@homeone-LX6810-01:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:22:68:3c:74:51   
           inet addr:192.168.2.77  Bcast:192.168.2.255  Mask:255.255.255.0  
           inet6 addr: fe80::222:68ff:fe3c:7451/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:148 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:68 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:18714 (18.7 KB)  TX bytes:19139 (19.1 KB)  
           Interrupt:47 Base address:0xa000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:1116 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:1116 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:85120 (85.1 KB)  TX bytes:85120 (85.1 KB)  
 

 homeone@homeone-LX6810-01:~$  
 now what? I'm new to linux

---

### Post by plucky on 2011-03-15
> eth0 Link encap:Ethernet HWaddr 00:22:68:3c:74:51
inet addr:192.168.2.77 Bcast:192.168.2.255 Mask:255.255.255.0 


Looks like you have a connection to your router


What happens if you right click on the Network Icon and make sure "Enable Networking" is ticked.

Also Right Click on the Network Icon and select "Edit Connections" and make sure "Connect Automatically" is ticked for the wired connection.

Also post output from a terminal for ```
sudo lshw -C network
``` will show what driver is loaded.


Good Luck

---

