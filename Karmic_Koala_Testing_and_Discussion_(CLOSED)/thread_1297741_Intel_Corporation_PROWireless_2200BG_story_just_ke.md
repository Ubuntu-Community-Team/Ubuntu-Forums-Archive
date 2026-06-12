---
title: "Intel Corporation PRO/Wireless 2200BG story just keeps getting worse"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by maheshasolkar on 2009-10-22
I am hoping it is not just me. But, my wireless woes keep getting worse.

It started around Alpha 5 when wireless connection was spotty and would disconnect randomly. Wireless would not connect if I was too far away from the router, but once established, I could move away. Now it is at a point where wireless connection is not established at all. Even when the laptop is right next to the router (99% signal strength as indicated in nm-tool output attached).

I have opened a bug on launchpad ([https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/450097](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/450097)), but it hasn't received much attention! 

Here's the lspci output pertaining to the wireless hardware:

```

02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 2751
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 6000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at e0206000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200

```

Attached are outputs of nm-tool and iwevent/daemon logs when the wireless connection fails. The access point I am trying to connect to is 'chord' (00:0D:88:BC:47:B9). It uses WPA2 Personal security and SSID broadcast is disabled. It is a D-Link DI-624 wireless router.

I am wondering if anyone else with similar hardware is running into these issues or can help me with mine. TIA.

---

### Post by maheshasolkar on 2009-10-22
Is there a good way to isolate router issues? My router is pretty old. However, a Mac connects to it over wireless too. The Mac's wireless connection is not completely without issues, but it connects and works most of the time.

I tried Jolicloud LiveCD on this laptop I am having issues with - and it connected just fine. That leads me to believe that both router and laptop's wireless hardware are in good shape.

---

### Post by bacardiandwatermelon on 2009-10-22
My 2200BG is working fine, I'm not hiding my SSID though and I am connecting to a Netgear WGR614.

---

### Post by maheshasolkar on 2009-10-22
Thanks for confirming that.

I should probably play with the router wireless settings. May be try out a new router.

It still bothers me that Jolicloud could connect to the same network, with the same hardware, effortlessly, but not Karmic. I am sure Jaunty will too - I am going to try that soon.

---

