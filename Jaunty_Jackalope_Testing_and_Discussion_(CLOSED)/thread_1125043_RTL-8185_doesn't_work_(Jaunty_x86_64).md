---
title: "RTL-8185 doesn't work (Jaunty x86_64)"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by doorknob60 on 2009-04-14
I'm building a computer for my friend, and a Newegg comment said that this card worked out of the box in Ubuntu for them, but that's not the case for me. This is the card:
```
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

It detects it and loads the rtl8180 module, and it shows up as wlan0, but it doesn't work.

```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Connection timed out
SIOCSIFFLAGS: Connection timed out
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:08:54:92:fa:c4
Sending on   LPF/wlan0/00:08:54:92:fa:c4
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down

```

It can't scan for networks either. Also, to make things worse, ndiswrapper fails to work with it altogether. It's using Kubuntu Jaunty x86_64. If I can't get it working soon, I'll have to try Arch or something, which IMO wouldn't be as good for my friend since he's not that great with computers.

EDIT: I just tried it in Arch, and it worked out of the box (with rtl8180 drivers), and it had HORRENDUS speeds, so I don't really care anymore. This is still likely a bug though, but I'm too lazy to report it.

---

