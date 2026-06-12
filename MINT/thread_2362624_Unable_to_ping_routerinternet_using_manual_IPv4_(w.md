---
title: "Unable to ping router/internet using manual IPv4 (wired)"
date: 2017-05-31
forum: MINT
---

### Post by bourne.aga1n on 2017-05-31
Hi,

I am having a strange problem trying to install Linux on this box - manual IPv4 (wired ethernet) gets activated successfully in the setup GUI (I think this is what you call anaconda), but I am unable to ping anything except localhost.

I have tried multiple Linux distributions, my last effort having been made today with Mint. No matter what distro, I am unable to ping the router (a.k.a default gateway) - 192.168.1.1, the all-important machine for me.

When I enter the host IP + netmask + gateway/router address, I see the message that the wired profile has been activated. But when I try to ping the router. I just get "Destination host not reachable".

As a result, I am unable to access internet and proceed with Linux installation.

Can anyone please help me fix the issue ? I have a lot of debugging information that can help drill down the issue, and am pasting it at the bottom of this post.

Since FreeBSD works like a charm on this box (and Windows XP used to work well till I moved from SATA to SSD), this would appear to be a Linux-specific issue.

Thanks for any help
Manish Jain


Here is output captured from Mint screens today : 

```
mint $ ifconfig -a
enp3s0 Link encap:Ethernet HWaddr 40:8d:5c:86:fa:18
inet addr:192.168.1.196 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::79ad:70b5:7c4c:ec1d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:34 errors:0 dropped:0 overruns:0 frame:0
TX packets:18 errors:0 dropped:376 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2898 (2.8 KB) TX bytes:1525 (1.5 KB)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:660 errors:0 dropped:0 overruns:0 frame:0
TX packets:660 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1
RX bytes:52247 (52.2 KB) TX bytes:52247 (52.2 KB)
```

```
mint $ ip route show
default via 192.168.1.1 dev enp3s0 proto static metric 100
169.254.0.0/16 dev enp3s0 scope link metric 1000
192.168.1.0/24 dev enp3s0 proto kernel scope link src 192.168.1.196 metric 100
Top
```

```
mint $ arping -D -c 3 -I enp3s0 192.168.1.1
ARPING 192.168.1.1 from 0.0.0.0 enp3s0
Sent 3 probes (3 broadcast(s))
Received 0 response(s)
```

```
mint $ echo $?
0
```

```
mint $ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.86 icmp_seq=1 Destination Host Unreachable
From 192.168.1.86 icmp_seq=2 Destination Host Unreachable
From 192.168.1.86 icmp_seq=3 Destination Host Unreachable
From 192.168.1.86 icmp_seq=4 Destination Host Unreachable
From 192.168.1.86 icmp_seq=5 Destination Host Unreachable
From 192.168.1.86 icmp_seq=6 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
8 packets transmitted, 0 received, +6 errors, 100% packet loss, time 7039ms
pipe 3
```

```
mint $ lscpi
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI 
bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI 
bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI 
bridge (PCI express gpp port D)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI 
bridge (PCI express gpp port H)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI 
bridge (external gfx1 port A)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] 
SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 
USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 
USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 
USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 
USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller 
(rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 
IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel 
HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC 
host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI 
Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 
USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 
USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 
USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor 
HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor 
Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor 
DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor 
Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor 
Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos 
[Radeon HD 6450/7450/8450 / R5 230 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio 
[Radeon HD 6400 Series]
02:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller 
(rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 
PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 
04)
05:00.0 Multimedia audio controller: C-Media Electronics Inc CMI8738/CMI8768 PCI 
Audio (rev 10)
05:00.1 Communication controller: C-Media Electronics Inc CM8738 (rev 20)
```

---

### Post by howefield on 2017-05-31
Thread moved to the "*MINT*" forum.

---

