---
title: "Thinkpad R400 8.10 beta installation report"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by Ævar Arnfjörð Bjarmason on 2008-10-16
I installed Ubuntu 8.10 beta[1] on a Lenovo TP R400, long story short neither the built-in Ethernet controller nor the wireless card work out of the box after installation and I haven't been able to bring either up using the modules that come built with the kernel.

pertinent lspci output:

> 00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)

The machine has a Intel Wireless Wifi Link 5100 card which doesn't show up in lspci output, I've been reading threads like [this one](http://ubuntuforums.org/showthread.php?t=879134) but haven't so far gotten it to work. In any case it's outside the scope of this installation report.

[Specs from the store (in Icelandic)](https://www.netverslun.is/Verslun/(S(qvanae3s5jgjmmbrc2ktho45))/product/TP-R400-P8400-2160-14W-Int-Com-6s-VBu,8537,327.aspx)
[General specs on ThinkWiki](http://www.thinkwiki.org/wiki/Category:R400)

1. ubuntu-8.10-beta-desktop-i386.iso (md5: 574c9b48dbb5cf471b05ff18a9adc082)

---

### Post by Ævar Arnfjörð Bjarmason on 2008-10-17
Long store short this now magically works and I'm not quite sure why because I didn't use properly controlled conditions.

Since the wireless card wasn't at first showing up in lspci output I thought I'd install and boot into Windows and install [the official drivers](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-70439) for the machine and see if the wireless card would show up. 

At first I installed the [drivers for the 5100 card]( http://www-307.ibm.com/pc/support/site.wss/MIGR-70505.html) which worked but the official IBM utility complained that it couldn't find the wireless card either. I was then prompted to go on a driver install rampage in an effort to eliminate devices with unknown status from Windows XP's device manager as I was beginning to suspect that the laptop didn't contain a wireless card at all, or that it wasn't plugged into the mini-pci socket on the motherboard.

After having installed almost all of them I rebooted to find that Windows XP detected new hardware, an unknown network device which turned out to be my wireless card once I had installed the driver package in Windows yet again.

I then rebooted into the 8.10 livecd to find that the wireless card was visible in lspci output, and that it worked flawlessly once I had modprobed the iwlagn module. The Ethernet still did not work however, but that's because the 8.10 livecd doesn't contain the e1000e driver, it only has the older e1000 version. Once booted into the installed system however the e1000e driver is available and Ethernet works too.

So the R400 works under Ubuntu 8.10 [beta] but I have no idea why, maybe the Windows drivers installed new firmware for the card, or maybe a cosmic ray passed through the wireless chipset at just the right time.

Here's the lspci output to prove it:

> 
avar@oe:~/src$ sudo lspci -nn -v -s 03:00.0 
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
	Subsystem: Intel Corporation Device [8086:1211]
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at f4300000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number b0-40-46-ff-ff-5d-21-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

avar@oe:~/src$ sudo lspci -nn -v -s 00:19.0 
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
	Subsystem: Lenovo Device [17aa:20ee]
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at fc000000 (32-bit, non-prefetchable) [size=128K]
	Memory at fc025000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1840 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] PCIe advanced features <?>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

> 
[    4.616400] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    4.616407] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    4.616489] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.616514] e1000e 0000:00:19.0: setting latency timer to 64
[    4.722919] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1e:37:da:bd:43
[    4.722926] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    4.722965] 0000:00:19.0: eth0: MAC: 5, PHY: 8, PBA No: 1008ff-0ff

> 
[   20.016184] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   20.016192] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   20.016324] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.016338] iwlagn 0000:03:00.0: setting latency timer to 64
[   20.016376] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   20.064409] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   20.069705] iwlagn 0000:03:00.0: PCI INT A disabled

---

