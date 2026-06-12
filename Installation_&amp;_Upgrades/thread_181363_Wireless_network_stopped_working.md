---
title: "Wireless network stopped working"
date: 2006-05-24
forum: Installation &amp; Upgrades
---

### Post by Nonno Bassotto on 2006-05-24
I have used hoary and Breezy, and I was happy with Ndiswrapper, and then NdisGtk, to make my PCMCIA wireless card work.
Now I have Dapper, and there is a little plus and a bgi minus.
The plus is that now my card starts networking immediately if I put it in when the PC is already on.
The minus is that it doesn't load at startup anymore. The system just hangs at the "configuring network interfaces" step, and no ctrl+c or ctrl+alt+del will work; I can only power down the system and leave my card out of the slot.
My etc/network/interfaces looks like this
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface wlan0 inet dhcp
wireless-essid CASA

auto wlan0

```
Has anyone any idea about what could break the system when loading? Also, how can I look when Ndiswrapper is actually loaded in the boot process?
I should also say that Ubuntu loaded for my card (also Breezy did this) an acx driver which didn't work. I had to use Ndiswrapper and blacklist acx to avoid conflict.

---

