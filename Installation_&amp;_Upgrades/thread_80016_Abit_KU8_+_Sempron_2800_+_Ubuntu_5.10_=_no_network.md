---
title: "Abit KU8 + Sempron 2800 + Ubuntu 5.10 = no network"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by koomina on 2005-10-21
I just bought a new PC with an Abit KU8 motherboard and an AMD Sempron 2800+ CPU. The KU8 motherboard includes an ALi M1689 chipset and an IC+ IP100A LAN controller.

Ubuntu 5.10 installed OK but did not detect the network interface. ifconfig shows lo but not eth0.

I tried "modprobe sundance" but it didn't help. Then I downloaded the Linux driver for the LAN controller from [http://www.icplus.com.tw/driver-pp-IP100A.html](http://www.icplus.com.tw/driver-pp-IP100A.html) but it won't compile. gcc reports lots of type errors and exits with error 1. (You have to change instances of "shell" to "sh" in the Makefile and mkdir /lib/modules/`uname -r`/build before saying "make all".)

Please help! Here is more info:

$ lspci

0000:00:00.0 Host bridge: ALi Corporation: Unknown device 1689
0000:00:01.0 PCI bridge: ALi Corporation: Unknown device 5246
0000:00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
0000:00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
0000:00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
0000:00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
0000:00:0e.1 IDE interface: ALi Corporation: Unknown device 5289 (rev 10)
0000:00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)
0000:02:0a.0 Ethernet controller: Sundance Technology Inc: Unknown device 0200 (rev 31)

$ cat /proc/cpuinfo

processor : 0
vendor_id : AuthenticAMD
cpu family : 15
model : 28
model name : AMD Sempron(tm) Processor 2800+
stepping : 0
cpu MHz : 1636.880
cache size : 256 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow lahf_lm
bogomips : 3235.84

---

### Post by koomina on 2005-10-22
I ended up borrowing a 3com 3c905B PCI network card from a friend, plugging it in, and reinstalling Ubuntu 5.10. Everything now works perfectly.

Hopefully, a future version of Ubuntu will support the ALi M1689 and the IC+ IP100A.

---

