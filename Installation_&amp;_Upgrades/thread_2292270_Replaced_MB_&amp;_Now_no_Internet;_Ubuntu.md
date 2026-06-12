---
title: "Replaced MB &amp; Now no Internet; Ubuntu"
date: 2015-08-26
forum: Installation &amp; Upgrades
---

### Post by bob1234567892 on 2015-08-26
I just replace a motherboard with an ASROCK N68C-GS4 FX.  I put an Opteron 1389 in it.  I installed Ubuntu 8.1.  When I boot it up, everything appears to be working except access to the internet.  I to my network via the motherboard with a Ethernet cable.  This setup was working fine with the old motherboard and CPU.
 
When I run ifconfig I get:
 
Lo     Link encap:Local Loopback
         Inet addr: 127.0.0.1
         In6 addr    ::1/128 scope : Host
         UP Loopback Running MTD:16436 Metric:1
          RX Packets:38 Error:0 Dropped: 0 Overruns: 0
          TX Packets:38 Errors:0 Dropped: 0 Overruns:0 Carrier:0
          Collisons: 0  txqueuele:0
           RX Bytes: 2727 (2.7 kB)  TX Bytes: 2728 (2.7 kB)
 
 
I am not very Linux adept.  
 
Any ideas how I solve this issue?

---

### Post by grahammechanical on 2015-08-26
Please confirm that you have installed Ubuntu 8.10? And it is not a typing error?  "I installed Ubuntu 8.1." Or perhaps you were thinking of Windows 8.1?

When we install Ubuntu we are asked to confirm that there is an internet connection. We are also invited to install updates as part of the installation process. We need an ethernet connection to the internet for those updates to be downloaded and installed.

Can you enter the BIOS/UEFI boot system settings utility and confirm that the ethernet adapter is not disabled?

Regards.

---

### Post by bob1234567892 on 2015-08-26
I am using Ubuntu 8.1.  I was running it from a USB stick before the motherboard replacement.  I have not reinstalled Ubuntu 8.1 onto the USB stick and was not asked if there was an internet connection.  I have gone into the Bios and can confirm that the LAN setting is enabled.

---

### Post by oldos2er on 2015-08-26
Ubuntu 8.10 is long out of support; please install a supported version of Ubuntu, 15.04 or 14.04 LTS.

---

### Post by bob1234567892 on 2015-08-26
It worked fine before the MB replacement.

---

### Post by wandalalakers on 2015-08-27
> **bob1234567892 said:**
> It worked fine before the MB replacement.

Just a guess but the driver for your nic card is no doubt not in Ubuntu 8.10 since this is a newer motherboard.
Like oldos2er said, install a later version of Ubuntu.

---

### Post by bob1234567892 on 2015-08-28
PCDoctor, your explanation seems to make sense.  I have reinstalled Ubuntu 8.1 and still have the same issue.  This PC is using Ubuntu 8.1 as part of the DOTSCH/UX v 1.2 ([http://www.dotsch.de/boinc/Dotsch_UX.html](http://www.dotsch.de/boinc/Dotsch_UX.html)  package to generate work for World Community Grid.  It has not been upgraded beyond Ubuntu 8.1. If I update the version of Ubuntu I don't know how to create a self standing Ubuntu WCG cruncher that does not use a hard drive.  As I said, I am not an avid Ubuntu/Linux user.

How can I do this?

---

### Post by bob1234567892 on 2015-08-28
Would installing an old NIC card in one of my slots work?

---

### Post by bob1234567892 on 2015-09-02
Anyone?

---

### Post by bob1234567892 on 2015-09-08
I have replaced the NIC with an old one.  I then went into the bios and directed it to not use the LAN built into the motherboard.

I still can't access the internet using Firefox.

I would appreciate any help understanding and resolving it.

When I run IFConfig, I now get:

Eth O Linkencap:Ethernet H Wadde 00:0D:88:1d:52:B8
UPBROADCAST Multicast MTU: 1500 Metric  1 
RXPackets:0 errors:0 dropped:0 overruns:0 Fterm:0
TXPackets:0 errors:0 dropped:0 overruns:0 carrier:0
Collisons:0 TSQueuelem: 1000
RXBytes:0 (0.0B) TXBytes:0 (0.0 B)
Interrupt:19 Base Address: 0xe800

Eth0: avahi Linkencap Ethernet HWaddr: 00:0d:88:1d:52:b8

inet addr: 169.254.6.85 Bcast: 169.254.255.255 Mask: 255.255.0.0
Up Broadcast mULTICAST mtu:1500 mETRIC 1
iNTERRUPT:19 bASE  ADDRESS: 0XE800

10 lINKENCAP: LOCAL LOOPBACK
INET ADDR: 127.0.0.1 Mask: 255.0.0.0
inet 6 addr:  : : 11258 Scope host
Up Loopback running MTU16436 Metric 1
RX Packets: 158 Errors:0 dropped: 0 Overruns: 0 Frame: 0
TXPAckets: 158 Errors:0 dropped: 0 Overruns: 0 Carrier :0
Collison:0 TXqueuelan:0
RX Bytes: 11576 (11.5 KB) TXBytes:11576 (11.5 KB)

---

### Post by MAFoElffen on 2015-09-08
Just a question: Is there a reason why you would want to stay with an old unsupported version of an OS, which is now vvulnerable to todays security risks?

Agreed that 8.10 proably does not have driver for your new hardware. To me (and others)... it is confusing why someone would have newer hardware and ignore the possibilities of what it could be. If you go back to what 8.10 supported, are you then using ethernet 10/10O instead of 1000?

What I was going to say before all the back and forth... Is to post the results of:
```

lspci -vnn
ifconfig -a

```

The reason you want to ask these on a motherboard swap these days, is that some baords will come up with the first eth port starting at eth2 or eth 3... I have one mobo here that has 3 onboard ports and started at eth4-eth6.

---

### Post by bob1234567892 on 2015-09-09
Please see below the results of running Lspci &#8211;vnn.

00:00.0 RAM  memory (0500}: nVidia Corporation MCP61 lpc 
Bridge (10de:03e2] (rev a1)
Subsystem: ASProck Incorporation device [1849:03e2]
Flags: bus master , 66 MHZ fastdevsel, latency 0
Capabilities: <access denied>

[LIST=1]
[*]isa Bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e1] (rev a2)
[/LIST]
00.01.1  SMBus [ 0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
Subsystem: ASRock Incorporation Device [1849:03eb] (rev a2)
Flags: 66 MHz, fast devsel, IRQ 11
I/O Ports at 0e00 [size=64]
I/O Ports at 0600 [size=64]
i/O ports at 0700 [size =64]
Capabilities: <access denied>
Kernel Driver in use: nForce2_sbus
Kernel Modules: i2c-nforce2
00.01.2   RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [110de:03ft] (rev a2)
Subsystem ASRock Incorporation Device [1849:03]

[LIST=1]
[*]USB Controller [0c03]: nVidia Corporation  MCP61 USB Controller [10de:03f:1] (rev a3) ( prog-if 10)
[/LIST]
Subsystem ASRock Incorporation  Device [1849:03fl]
Flags: bus msaster, 66 MHz, fast devsel, latency 0, IRQ 22
Memory at efeff000 (32bit, nonprefetable) [Size 4K]
Capabilities: <access denied>
Kernel Driver in use: ohci_hcd
Kernel modules: ohci_hd

[LIST=1]
[*]USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3) (prog-if20)
[/LIST]
Subsystem: ASRock Incorporation Device [1849:03f2]
Flags bus master, 66 MHz, fast devsel, latency 0, IRQ 23
Memory at efefec00 (32 bit nonprefetchable) (size=256)
Capabilities: <access denied>
Kernel Driver in use: ehci_hcd
Kernel modules: ehci-hcd
00.04.0 PCI Bridge [0604]: nVida Corporation MCP61 PCI Bridge [10de:03f3] (rev a1) (prog-if 01)
Flags: busmaster, 66 MHz, fast devsel, latency 0
Bus: Primary =00, secondary=01, subordinate =01, sec-latency=32
I/O behind Bridge: 0000e000-0000efff
Memory behind Bride: eff00000-efffffff
Capabilities: <access denied>
00.05.0 Audio device[0403]:nVidia Corporation MCP61 High Definition Audio [10de:03f0] 9rev a2)
Subsystem: ASPock Incorporation Device [1849:7662]
Flags: busmaster, 66 MHz, fast devsel, latency 0,IRQ 22
Memory at efef8000 (32 bit non prefetchabel)( (Size 16K)
Capabilities: ,access denied>
Kernel driver in use: HDA-Intel
Kernel modules: slmd-had-intel
00.06.0   IDE Interface [0101]:nVidia Corporation MCP61 IDE [10de:03ec] (reva2) (prog-if 8a MasterSec P PriP])
Subsystem: Device [f849:03ec]
Flags: Busmaster, 66 MHz fast devsel, latency 0
[virtual] memory at 00000H0 (32 bit, non prefetchable) [disabled] [size=8]
[virtual] memory at 00000f0 (type 3, non prefetchable) [disabled] (size=1)
[virtual] memory at 00000170 (32 bit, non prefetchable) [disabled] (size=8)
[virtual} memory at 00000370 (type 3, nonprefetchable) [disable] (size =1)
I/o Ports at ffa0 [size 16]
Capabilities: <access denied>
Kernel Driver in use: pata_amd
Kernel Modules: ata_generic, pata_amd, pataacpi
00.08.0 IDE Interface [0101]:; nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2) (prog-if 85 [Master Sec 0 Pri 0])
Subsystem: ASRock Incorporation Device [1849:03f6]
Flags: busmaster. 66 MHz, fast devsel, latency 0, IRQ 21
I/o Ports at d0860 [size=8]
I/o Ports at d000 [size=4]
I/o Ports at cc00 [size=8]
I/o Ports at c880 [size = 4]
I/o Ports at c800 [size=16]
Memory at efefd000 (32 bit non prefetchable) [size=4k]
Capabilities:  <access denied>
Kernel drivers in use:  SATA_NV
Kernel Mobile: ata_generic, pata_acpi, sata-n
00.08.1 IDE interface nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2) (prog-if 85[Master Sec 0 Pri 0)]
Subsystem: ASRock Incorporation Device [1849:03f6]
Flags: busmaster, 66 MHz, fast devsel, latency 0, IRQ 20
I/O Ports at c480 [size=8]
I/O Ports at c400 [size=4]
I/O Ports at c080 [size=8]
I/O Ports at c000 [size=4]
I/O Ports at bc00 [size=16]
Memory at efefc000 (32 bit, nonprefetchable) [size 4k]
Capabilities: <access denied>
Kernel Driver in use: sata nv
Kernel modules: ata generic, pata acpi, sata n
00.09.0 PCI Bridge [0604]: nVidia Corporation MCP61 PCI Express Bridge [10de:03e8] (rev a2)
Flags: busmaster, fast devsel, latency 0
Bus: primary=01, secondary=02, subordinate=02 sec-latenncy=0
Capabilities: <access denied>
Kernel driver in use: pci eport_drice
Kernel modules: shpchp
 
00.0b.0 PCI Bridge [0604] nVidia Corporation MCP61 PCI Express bridge [10de:03e:9] (rev a2)
Flags: busmaster, fast devsel, latency 0
Bus: primary = 00, secondary =03, subordinate=03, sec-latency=0
Capabilities: <access denied>
Kernel driver in use: pcieport.driver
Kernel Modules: shpchp
00.0d.0 Vga compatible controller [0300]: nVidia Corporation Device [10de:03d6] (rev a2)
Subsystem: ASRock Incorporation Device [1849:03d6]
Flags: busmaster, 66 MHz, fast devsel, latency 0, IRQ 23
Memory at dd000000 (32 bit nonprefetchable) [size=16M]
Memory at d0000000 (64 bit nonprefetchable) [size=256M]
Memory at ed0000000 (64 bit nonprefetchable) [size=16M]
[virtual] expansion ROM at efec0000 [disabled] (size=128k)
Capabilities: <access denied>
Kernel driver in use: nvidia
Kernel modules: nvidia, nvidiafb
00.18.0  Hot Bridge [0600]: Advanced Micro Devices (AMD) Family 10h [Opteron, Athlon 64, Sempron] Hypertransport Configuration [1022:1200]
Flags: fert devsel
Capabilities: <access denied>
00.18.1 Hot Bridge [0600]: Advanced Micro Devices (AMD) Family 10h [Opteron, Athlon 64, Sempron] Address Map [1022:1201]
Flags: Fast devsel
00.18.2 HostBridge [0600]: Advanced Micro Devices (AMD) Family 10h [Opteron, Athlon 64, Sempron] DRAM Controller [1022:1202]
Flags: Fast Devsel
00.18.3 Host Bridge [0600]: Advanced Micro Devices (AMD) Family 10h [Opteron, Athlon 64, Sempron] Miscellaneous Control [1022:1203]
Flags: fast devsel
Capabilities: <access denied>
00.18.4 Host Bridge [0600]: Advanced Micro Devices (AMD) Family 10h [Opteron, Athlon 64, Sempron] Link Control [1022:1204]
Flags: fast devsel
01.08.0 Ethernet Controller [0200] Plink  System Inc RTL8139 Ethernet [1186:1300] (rev 10)
Subsystem: DLink System Inc Device [1186:1301]
Flags: busmaster, medium devsel, latency 32, IRQ 19
I/O Ports at 0800 [size:256]
Memory at effffc00 (32 bit, nonprefetable) size = 256)
Capabilities: <access denied> 
Kernel Drivers in use: 8139too
Kernel modules: 8139too

---

### Post by bob1234567892 on 2015-09-17
So that wasn't useful in solving the issue?

---

### Post by MAFoElffen on 2015-09-18
Still waiting on the results of 
```

ifconfig -a

```
Right?

And since the output said "Capabilities: Access Denied", instead try
```

sudo lspci -vnn | grep -i "Ethernet" -A 5
sudo lshw -n -c network

```

This time, when you go to post output or commands... Please use the Advanced Post menu > Press the "[SIZE=5][FONT=arial black]**#**[/FONT][/SIZE]" icon (code tags) and paste those between the [ code ]  and [ /code ] tags.

---

### Post by bob1234567892 on 2015-09-21
ifconfig -a
```

```
eth0 Linkencap: Ethernet HWAddr: 00:0d:88:1d:52:b8
Up Broadcast Multicast MTU:1500 Metric:1
RXPackets:0 errors:0 dropped:0 overruns:0 frame:0
TXPackets: 0 errors:0 dropped:0 overruns:0 carrier:0
collisions: 0 TXqueuelen:1000
RX Packets:0 (0.0 kB) TXBytes :0 (0.0 kB)
Interrupt:19 Baseaddress: 0xe800

ETH0:avahi Linkencap:Ethernet HWAddr: 00:0d88:1d52:b8
inet addr: 127.0.0.1 Mask:255.0.0.0
inet6addr: :: 1/128 Scope: Host
Up loopback running MTU:16436 Metric:1
RXpackets:46 errors:0 dropped:0 overruns:0 frame:0
TXPackets: 46 errors:0 dropped:0 overruns:0 carrier:0
collision.0 txqueue:0
RX Bytes: 3320 (3.3 kB) TXBytes 3320 (3.3 kB)

---

### Post by MAFoElffen on 2015-09-22
This part confirms that it si not getting assigned an IP or subnet address. 

The second part of that I asked you to post in my last post (which you skipped, please reread and post it) should display what, if any, driver it is trying to use for that NIC. I asked you to post that part to see if it is trying to use a driver... or if it just cannot find one. 

Did you try to set a static address or it it still DHCP (automatically assigned)? To confirm that, please post your /etc/network/interfaces file.

To jump ahead (since you have a delay in your responses) please post the result of:
```

lsmod | grep 8139

```
There are 2 different drivers that have supported that card for years now, just wanting to see which of the two is being loaded...

---

### Post by bob1234567892 on 2015-09-22
lsmod | grep 8139

8139too 35968 0
mii 14592  1 8139too

---

### Post by bob1234567892 on 2015-09-22
```

```

sudo lspci -vnn |grep -I "Ethernet" -A 5

01:08.0 Ethernet Controller [0200]:Dlink System INc RTL 8139 Ethernet [1186:1300] (rev10)
subsystem: DLink System Inc Device [1186:1301] 
Flags: busmaster, medium devsel, latency 32, IRQ 19
I/o Ports at e800 [size=256]Memory at effffc00 [size=256]
Memory at effffc00 (32 bit, non prefetchible) [size=256
Capabilities: [50] Power management version 2

---

### Post by bob1234567892 on 2015-09-22
In the  letc|network|interfaces file is:

```

```# Used by ifup(8) and ifdown (8).  See the interface (5) manpage or
# |wrlshar|doc|ifupdown|examples for more information

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto eth3
iface eth3 inet dhcp```

```

---

### Post by bob1234567892 on 2015-09-22
```

```
sudo lshw -n -c network

Hardware lister (lshw) -B.02.13
usage:lshw [-format] [-options]
lshw -version
-version print program version (B.02.13)
 
format can  be 
-html output hardware tree as HTML
-xml  output hardware tree as XML
-short output hardware paths
-businfo output bus info 

options can be: 
- class CLASS only show a certain class of hardware
- C CLAS means class CLASS
- disable TEST disable & test (like pci, isapp, cpid, etc.)
- enable TEST enable test 
- disable TEST disable & test
- quiet don't show display status.
- sanitize sanitize output (remove sensitive information like serial numbers, etc.)
- numeric output numeric ids (for pci, usb, etc.)

---

### Post by bob1234567892 on 2015-09-30
Does this shed any light on the issue?

---

