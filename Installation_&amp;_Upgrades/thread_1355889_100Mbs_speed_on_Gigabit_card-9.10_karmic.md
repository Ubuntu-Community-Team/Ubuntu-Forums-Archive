---
title: "100Mb/s speed on Gigabit card-9.10 karmic"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by waffletten on 2009-12-15
I just did a new install of 9.10 on my acer apire revo and everything works great, except.

The wired connection (eth0) is showing up as 100Mb/s when it is a Gigbit connection.  Why is this and how do I fix it.  This was no problem when I had 8.04 and 9.04 on this computer.

says the forcedeth driver is used for connection on eth0

output from lspci:
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 [COLOR=Red]Ethernet controller: nVidia Corporation MCP79 Ethernet [/COLOR](rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by waffletten on 2009-12-15
Ignore this thread, I realized that the eth0 wasn't the possible speed of my network card (GB/s) but the speed of my network(100Mb/s). Figured out once I had posted my moronic question.

---

