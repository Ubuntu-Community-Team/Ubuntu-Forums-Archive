---
title: "WOL Forcedeth 0.61 Jaunty"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Lynnae on 2009-03-03
**Problem:** WOL doesn't work after shutting down with Linux.
It does work after shutting down from Windows Vista (Dualboot) or by shutting down before grub is even started/loaded.

**Hardware:** [Asus P5N-E Sli]("http://www.asus.com/products.aspx?modelmenu=2&model=1474&l1=3&l2=11&l3=473&l4=0")

**lspci:** 00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

**Ethtool eth0:** 	Supports Wake-on: g
	Wake-on: g

**Halt/Reboot scripts:** -i removed.

**modprobe -l | grep forcedeth:** /lib/modules/2.6.28-8-generic/kernel/drivers/net/forcedeth.ko

**dmesg | grep forcedeth:**
[    2.032813] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.033151] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 21 (level, low) -> IRQ 21
[    2.033156] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.553127] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr XX:1f:c6:8c:e9:XX
[    2.553130] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3


I'm using Jaunty alpha right now.
Reversing the mac address had no effect either.

Any ideas are highly appreciated :3

---

