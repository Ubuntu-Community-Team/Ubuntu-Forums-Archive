---
title: "Nasty Bug In Hardy Proposed"
date: 2008-06-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-06-22
Hi folks. Im on Hardy proposed and doing some testing. Ive found a nasty bug where my wired ethernet will stop working.

My desktop machine is set to never sleep. However, after a period of time with no network use through my wired via rhine ii nic (eth0), ACPI thinks IRQ 23 isnt needed. ACPI turns off IRQ 23, eth0 times out and wont come back without a reboot. ifdown/ifup wont fix it.

Kernel log:

Jun 21 03:04:07 ppp kernel: [   57.447218] eth0: no IPv6 routers present
Jun 21 04:29:46 ppp kernel: [ 5193.747505] irq 23: nobody cared (try booting with the "irqpoll" option)
Jun 21 04:29:46 ppp kernel: [ 5193.747514] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
Jun 21 04:29:46 ppp kernel: [ 5193.747516] 
Jun 21 04:29:46 ppp kernel: [ 5193.747517] Call Trace:
Jun 21 04:29:46 ppp kernel: [ 5193.747519]  <IRQ>  [__report_bad_irq+0x1e/0x80] __report_bad_irq+0x1e/0x80
Jun 21 04:29:46 ppp kernel: [ 5193.747550]  [note_interrupt+0x2ad/0x2e0] note_interrupt+0x2ad/0x2e0
Jun 21 04:29:46 ppp kernel: [ 5193.747562]  [handle_fasteoi_irq+0xa1/0x110] handle_fasteoi_irq+0xa1/0x110
Jun 21 04:29:46 ppp kernel: [ 5193.747571]  [do_IRQ+0x7b/0x100] do_IRQ+0x7b/0x100
Jun 21 04:29:46 ppp kernel: [ 5193.747577]  [ret_from_intr+0x0/0x0a] ret_from_intr+0x0/0xa
Jun 21 04:29:46 ppp kernel: [ 5193.747583]  [pci_conf1_read+0x0/0x100] pci_conf1_read+0x0/0x100
Jun 21 04:29:46 ppp kernel: [ 5193.747596]  [__do_softirq+0x60/0xe0] __do_softirq+0x60/0xe0
Jun 21 04:29:46 ppp kernel: [ 5193.747609]  [call_softirq+0x1c/0x30] call_softirq+0x1c/0x30
Jun 21 04:29:46 ppp kernel: [ 5193.747614]  [do_softirq+0x35/0x90] do_softirq+0x35/0x90
Jun 21 04:29:46 ppp kernel: [ 5193.747618]  [irq_exit+0x88/0x90] irq_exit+0x88/0x90
Jun 21 04:29:46 ppp kernel: [ 5193.747621]  [do_IRQ+0x80/0x100] do_IRQ+0x80/0x100
Jun 21 04:29:46 ppp kernel: [ 5193.747624]  [default_idle+0x0/0x40] default_idle+0x0/0x40
Jun 21 04:29:46 ppp kernel: [ 5193.747628]  [default_idle+0x0/0x40] default_idle+0x0/0x40
Jun 21 04:29:46 ppp kernel: [ 5193.747630]  [ret_from_intr+0x0/0x0a] ret_from_intr+0x0/0xa
Jun 21 04:29:46 ppp kernel: [ 5193.747633]  <EOI>  [lapic_next_event+0x0/0x10] lapic_next_event+0x0/0x10
Jun 21 04:29:46 ppp kernel: [ 5193.747648]  [default_idle+0x29/0x40] default_idle+0x29/0x40
Jun 21 04:29:46 ppp kernel: [ 5193.747654]  [cpu_idle+0x6f/0xc0] cpu_idle+0x6f/0xc0
Jun 21 04:29:46 ppp kernel: [ 5193.747662]  [start_kernel+0x2c5/0x350] start_kernel+0x2c5/0x350
Jun 21 04:29:46 ppp kernel: [ 5193.747670]  [x86_64_start_kernel+0x12e/0x140] _sinittext+0x12e/0x140
Jun 21 04:29:46 ppp kernel: [ 5193.747678] 
Jun 21 04:29:46 ppp kernel: [ 5193.747679] handlers:
Jun 21 04:29:46 ppp kernel: [ 5193.747680] [usbcore:usb_hcd_irq+0x0/0x60] (usb_hcd_irq+0x0/0x60 [usbcore])
Jun 21 04:29:46 ppp kernel: [ 5193.747702] [via_rhine:rhine_interrupt+0x0/0x7f0] (rhine_interrupt+0x0/0x7f0 [via_rhine])
Jun 21 04:29:46 ppp kernel: [ 5193.747710] Disabling IRQ #23
Jun 21 04:34:46 ppp kernel: [ 5493.104588] NETDEV WATCHDOG: eth0: transmit timed out
Jun 21 04:34:46 ppp kernel: [ 5493.104738] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jun 21 04:34:46 ppp kernel: [ 5493.105384] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun 21 05:05:02 ppp kernel: [ 7308.203455] NETDEV WATCHDOG: eth0: transmit timed out
Jun 21 05:05:02 ppp kernel: [ 7308.203606] eth0: Transmit timed out, status 1003, PHY status 786d, resetting...
Jun 21 05:05:02 ppp kernel: [ 7308.204254] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun 21 05:35:16 ppp kernel: [ 9121.303308] NETDEV WATCHDOG: eth0: transmit timed out
Jun 21 05:35:16 ppp kernel: [ 9121.303457] eth0: Transmit timed out, status 1003, PHY status 786d, resetting...
Jun 21 05:35:16 ppp kernel: [ 9121.304106] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun 21 06:05:32 ppp kernel: [10936.402170] NETDEV WATCHDOG: eth0: transmit timed out
Jun 21 06:05:32 ppp kernel: [10936.402319] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jun 21 06:05:32 ppp kernel: [10936.402968] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun 21 06:12:40 ppp kernel: [11364.189787] NETDEV WATCHDOG: eth0: transmit timed out
Jun 21 06:12:40 ppp kernel: [11364.189937] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jun 21 06:12:40 ppp kernel: [11364.190589] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun 21 06:36:06 ppp kernel: [12769.492097] NETDEV WATCHDOG: eth0: transmit timed out
Jun 21 06:36:06 ppp kernel: [12769.492247] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jun 21 06:36:06 ppp kernel: [12769.492892] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun 21 07:06:22 ppp kernel: [14584.590959] NETDEV WATCHDOG: eth0: transmit timed out
Jun 21 07:06:22 ppp kernel: [14584.591109] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jun 21 07:06:22 ppp kernel: [14584.591757] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun 21 07:36:36 ppp kernel: [16397.690817] NETDEV WATCHDOG: eth0: transmit timed out
Jun 21 07:36:36 ppp kernel: [16397.690967] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jun 21 07:36:36 ppp kernel: [16397.691615] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun 21 08:06:54 ppp kernel: [18214.788695] NETDEV WATCHDOG: eth0: transmit timed out
Jun 21 08:06:54 ppp kernel: [18214.788846] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jun 21 08:06:54 ppp kernel: [18214.789492] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

My lspci:

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
	Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 23
	Region 0: I/O ports at 9400 [size=256]
	Region 1: Memory at dffff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

---

### Post by olskar on 2008-06-22
Put that on launchpad and be sure to include that you have hardy-proposed enabled.

---

### Post by ronacc on 2008-06-22
how long do you have to have 0 net activity to timeout ETH0 ? I will try to confirm but I will have to shutdown a few things that access the net every 5 minutes or so to bring my activity to 0 .

---

### Post by Nullack on 2008-06-22
Thanks for the attempt to replicate, very much appreciated :)

I'd say about an hour.

You need to have a default ACPI config - not turned off in CMOS or disabled via some sort of tweaked boot startup.

It may very well be specific to my Via chipset - interesting to see what yours does and what chipset youve got.

---

### Post by ronacc on 2008-06-22
here is my lspci , I haven't messed with my bootup or cmos settings . I'm starting the hour as soon as I post this .

ron@ron-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
ron@ron-desktop:~$

---

### Post by ronacc on 2008-06-22
Ok I let it run for 2 hrs with no internet activity ( actualy no activity at all I was outside working on something . ETH0 did not go away on my system , so it may be related to your specific setup .

---

### Post by cariboo on 2008-06-22
I think this is a problem with via rhine chipset. I have one on the mb of my server and it will stop for no reason at all. The only way to get it working again is to do a hard reset. This can be a real pain as my server is running headless in an inaccessible corner. I solved the problem by installing an inexpensive rtl based nic. I sort of inherited this motherboard from a former employer and it was a problem for as long as it was in service, Previously it was running XP and whenever network access stooped the bookkeeper would just hit the reset button and continue on after it had rebooted.

Jim

---

### Post by Gina on 2008-06-22
In that case it would seem to be a hardware problem and the only solution would be to disable the MB nic and put a separate one in.  I had to do that with one of my machines.

---

### Post by Nullack on 2008-06-22
Ronacc thanks for trying to replicate. Ok so it's hardware specific.

Whats interesting is that the nic works fine on Vista. That proves that atleast some sort of code will work on it.

---

### Post by ronacc on 2008-06-22
if it didn't work with windows they'd be out of buisness , unfortuately they don't have that much incentive yet to provide decent support for linux although they are making noises about doing so .

---

### Post by Nullack on 2008-06-24
Well Im not getting any help with my bug report on launchpad but nonetheless Im perservering with this. I hope that if I put some time into this that atleast one thing someone else wont have a hassle with when using this via nic on acpi.

I did some more testing where I compiled the latest vanilla kernel 2.6.25.8 and I confirmed its an upstream kernel problem. I joined the acpi kernel mailing list and was asked to boot with the irq polling boot option and if that fixes is to bug report it on the kernel bugzilla.

---

### Post by Nullack on 2008-06-26
Just an update.....

Considering that hardy proposed has kinda settled now for hardy's point release, I upgraded to Intrepid pre-alpha.

There's obviously a few rough edges but at this stage - YES! My system has been up for over 16 hours with no loss of eth0!!!!!!

So maybe the new acpi versions have something to do with it.

Anyway I dont want to declare this problem as fully over until more time has passed but it looks promising :popcorn:

---

### Post by soccerboy on 2008-06-26
> **Nullack said:**
> Just an update.....

Considering that hardy proposed has kinda settled now for hardy's point release, I upgraded to Intrepid pre-alpha.

There's obviously a few rough edges but at this stage - YES! My system has been up for over 16 hours with no loss of eth0!!!!!!

So maybe the new acpi versions have something to do with it.

Anyway I dont want to declare this problem as fully over until more time has passed but it looks promising :popcorn:

See Linus's blog on updates to network connectivity and drivers in the latest kernel.  Don't have the link right of the bat.

---

### Post by Nullack on 2008-06-28
Waaaa :(

Woke up this morning with no IP and spammed up log about netdev watchdog timeouts on eth0

This is on intrepid, dammit!!

---

