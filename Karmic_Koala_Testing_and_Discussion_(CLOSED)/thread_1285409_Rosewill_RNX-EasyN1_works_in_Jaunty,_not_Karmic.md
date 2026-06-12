---
title: "Rosewill RNX-EasyN1 works in Jaunty, not Karmic"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by charrah on 2009-10-07
My USB wireless adapter works fine when I'm using Ubuntu Jaunty, but not the new Karmic beta. A possibly important detail is that it doesn't appear to get its own /dev file. I think it uses the rt2870sta  or rt3070sta driver, not entirely certain. It appears in the network manager as the Ralink 802.11 n WLAN but no networks are listed under it (in Jaunty it lists quite a few). So how do I make it work with the Karmic beta?

---

### Post by charrah on 2009-10-09
Bump. When I plug it in, I get this in dmesg:
```
[23953.056328] usb 1-6: new high speed USB device using ehci_hcd and address 7
[23953.205652] usb 1-6: configuration #1 chosen from 1 choice
[23953.237284] phy2: Selected rate control algorithm 'minstrel'
[23953.239449] Registered led device: rt2800usb-phy2::radio
[23953.239487] Registered led device: rt2800usb-phy2::assoc
[23953.239534] Registered led device: rt2800usb-phy2::quality
[23953.529434] rt2800usb 1-6:1.0: firmware: requesting rt2870.bin
[23953.973433] ADDRCONF(NETDEV_UP): wlan1: link is not ready

```

---

### Post by charrah on 2009-10-15
Added this to my /etc/modprobe.d/blacklist.conf and now it works :) I didn't really know what I was doing though...
```
blacklist rt2800usb
blacklist rt2870sta
```

---

### Post by wch on 2009-10-16
This works great - thank you! How'd you figure it out?

---

### Post by charrah on 2009-10-16
(Sorry I am caught in a bit of an identity game here- I posted this solution on Launchpad, here, and Linuxforums)

On checking dmesg again, I found that important line:
```
[ 8566.396547] Error: Driver 'rt2870' is already registered, aborting...
```
What it looked like to my inexperienced eye was that two drivers were trying to take responsibility for the hardware. So I thought maybe if I blacklisted the other drivers the one that should load (rt3070sta I think; this at least was the name of the driver that I tried to compile from Ralink's site, though make had errors) would do so properly. I didn't really know the correct name of the overeager driver because rt2870 isn't a module name, but rt2800usb and rt2870sta are. So I put both down for good measure.

---

