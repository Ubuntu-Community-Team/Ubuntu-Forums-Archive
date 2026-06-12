---
title: "Wireless, wicd keeps dropping out then fails to reconnect."
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-03-14
Have to reboot or take laptop next to router for it to reconnect.

---

### Post by philinux on 2009-03-15
Still having to reboot to get connection back.

A refresh say not wireless networks available but rebooting connects with signal 65% from same location.

---

### Post by taavikko on 2009-03-15
> **philinux said:**
> Have to reboot or take laptop next to router for it to reconnect.

Are you certain that it isn't your wireless driver that's acting up.
Rather than wicd.

What card? Chipset? Driver?
Encryption?

**lshw -C network**

---

### Post by philinux on 2009-03-15
Not sure what that problem is. Wireless is always a pain but here's some info. When it's working it's fine. It's when it drops out is the pain. It's likely to be signal strength dropping off but I've set it to auto reconnect. It does if right next to router. Away from router have to reboot.

```
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
```


```
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:5a:57:27
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:08:0d:a6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9e:2d:70:8a:4d:bc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

### Post by taavikko on 2009-03-15
Your prints didn't show your wireless card,

lspci output was the wired one.

But if I remember correctly, there was some issues with r8139too driver...
Just can't remember :( Anyone?

does dmesg print anything when connection drops?

Could you attach **dmesg > ~/dmesg.txt**
So we could take a peek?

---

### Post by philinux on 2009-03-21
Back at Gf's. Laptop wireless still dropping out and refuses to reconnect without a reboot.

dmesg shows this..
```

[ 1822.320044] wlan0: No ProbeResp from current AP 08:10:73:0b:6d:1e - assume out of range
[ 1823.971275] wlan0: direct probe to AP 08:10:73:0b:6d:1e try 1
[ 1823.983538] wlan0: direct probe to AP 08:10:73:0b:6d:1e try 1
[ 1824.180055] wlan0: direct probe to AP 08:10:73:0b:6d:1e try 2
[ 1824.380057] wlan0: direct probe to AP 08:10:73:0b:6d:1e try 3
[ 1824.580049] wlan0: direct probe to AP 08:10:73:0b:6d:1e timed out
[ 1836.920077] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1837.166080] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1838.691404] wlan0: direct probe to AP 08:10:73:0b:6d:1e try 1
[ 1838.691432] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1838.888049] wlan0: direct probe to AP 08:10:73:0b:6d:1e try 2
[ 1838.888083] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1839.088049] wlan0: direct probe to AP 08:10:73:0b:6d:1e try 3
[ 1839.088085] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1839.288043] wlan0: direct probe to AP 08:10:73:0b:6d:1e timed out
[ 1839.288051] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
```

---

### Post by Bert Mariën on 2009-03-21
I didn't really follow the issue here, but for some cards you have to/
---+---
Add to /etc/rc.local

ifconfig wlan0 up
iwconfig wlan0 rate 54M fixed

exit 0
---+---
before they work ok&y.

---

### Post by philinux on 2009-03-21
Ok done, I'll be back if that doesn't work. But cheers anyway.

---

### Post by philinux on 2009-03-22
Still not reconnecting, have to reboot.
[edit] have to reboot sometimes. Other times it will reconnect. Could it just be wireless being wireless. i.e. a royal pain. lol

---

