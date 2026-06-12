---
title: "[SOLVED] Feisty Install - No Network Connection"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by willy1946 on 2007-08-21
I am a newby linux user who just installed Feisty in a multi-boot setup with Win XP and Win Vista. The installed Feisty boots up OK but I have no network or internet connection. The port connection light on my router will not even light. Win XP and Vista on the same computer both boot fine with full network and internet connection. Booting from the Feisty Live CD, as well as live CD's for both Edgy and Fedora 7 all fail in the same way, so at least they are consistent.

    I also tried booting the Feisty live CD in my laptop which is also hardwired to the same router but on it I get full network and internet connection, so the problem must be something to do with the hardware setup on my desktop.

    I have searched the forum and found similar problems to mine but no solution that works for me, so I am resorting to crying for help to try and get my connection up and running. I hope someone can help me out.

My computer configuration is as follows:
Computer:	Acer Aspire T135
MOBO:		 Giga-Byte GA-K8VM800M
Ethernet:	 On-board Realtek RTL-8139 MAC 00:0F:EA:41:5D:01 hardwired to router
CPU:		   AMD Sempron
Display:          NVidia GForce 6600  in AGP slot
Modem:		Motorola SB5100 Cable Modem connected to WAN port of router
Router:		 D-Link DIR 655 Extreme-N, DHCP server enabled, IP 192.168.1.1
OS Config:	Feisty in multi-boot setup with Win XP and Win Vista. XP and Vista have no problem                                                        
                       connecting to network and internet

To try and anticipate some questions, I include the output from some commands in Feisty which might provide a clue:

**$ lshw | grep network**
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 13
             bus info: pci@00:13.0
             logical name: eth0
             version: 10
             serial: 00:0f:ea:41:5d:01
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 
                                autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 
                                duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes 
                                port=MII speed=100MB/s
             resources: ioport:c000-c0ff iomemory:e7005000-e70050ff irq:18

**$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:41:5D:01  
          inet6 addr: fe80::20f:eaff:fe41:5d01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth0:avah Link encap:Ethernet  HWaddr 00:0F:EA:41:5D:01  
          inet addr:169.254.4.32  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67100 (65.5 KiB)  TX bytes:67100 (65.5 KiB)

**$ lspci**
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0b.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0b.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0b.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0b.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)

**$ route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
link-local      *               255.255.0.0     U         0 0          0 eth0
default         *               0.0.0.0         U         0 0          0 eth0

**$ cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
[B]
$ ping 192.168.1.1[/B]
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.4.32 icmp_seq=2 Destination Host Unreachable
From 169.254.4.32 icmp_seq=3 Destination Host Unreachable

**$ sudo dhclient**
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0f:ea:41:5d:01
Sending on   LPF/eth0/00:0f:ea:41:5d:01
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by TB2 on 2007-08-21
This might be easy:

Go into XP, device manager and enable "Wake-On-Lan" on the realtek controller. It might do the trick. It's a known problem with the NIC being turned of by windows on shutdown, and not being reactivated by the Linux drivers. This workaround did the trick for me. Alternatively you can just turn of the machine and cut it's power for a few seconds, which should reset the NIC. (pull the plug or the batteries, depending...)

Sorry if it doesn't help...

---

### Post by willy1946 on 2007-08-21
Thanx TB2! That did the trick. THis time, when I logged off Windoze, the connection light on the router stayed lit. I wasn't too sure what parm you were referring to, tho. In the Advanced tab of the NIC properties, there was no Wake-on-LAN. There WAS three other parms. WakeUp on ARP/PING (already enabled), WakeUp on Link Change (disabled), and WakeUp using APM Mode (disabled). Just to be sure, I enabled the two that were disabled). I don't know which one worked.
  
Is this a bug in Linux? Is there not some command that can be issued from within Linux to wake up the NIC. It seems to me this is a problem that could bite anyone trying to install Linux in a dual boot Windoze-Linux setup. The parms I changed are not turned on by default.

---

### Post by Pumalite on 2007-08-21
I'd say is a bug in windblows. Windoze should free the connection on shut down.

---

### Post by willy1946 on 2007-08-21
You may be right. If so, it is even worse in Win Vista. In there, the same options are available, but turning them on STILL results in the NIC being turned off.  This means if I want to go from Vista to Feisty, I have to log off Vists, boot into the XP logon screen, logoff again, and then boot Feisty. What a pain in the a***.

---

### Post by Pumalite on 2007-08-21
Don't you think is time to leave Micro**** behind?

---

