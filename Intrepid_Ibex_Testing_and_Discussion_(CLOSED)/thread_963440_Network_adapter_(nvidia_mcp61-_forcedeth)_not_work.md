---
title: "Network adapter (nvidia mcp61- forcedeth) not working"
date: 2008-10-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by giancarlo76 on 2008-10-30
This is an excerpt of lspci -v:
```
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 220
	Memory at dfefd000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d480 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

```

NetworkManager says it's connected, but dhclient actually fails getting IP address. This is the output:
```
# sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No buffer space available
Listening on LPF/eth0/00:1f:c6:a7:e0:0a
Sending on   LPF/eth0/00:1f:c6:a7:e0:0a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Message too long
```

Any hint to solve this issue?
Thanks.

---

