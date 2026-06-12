---
title: "Network problem after upgrading 7.04 to 7.10"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by apjr1970 on 2007-10-25
Hey Guys.

I recently installed Ubuntu 7.04 and liked it so much I decided to upgrade to 7.10.
I downloaded all the updates to 7.04 and I was asked if I'd like to upgrade to 7.10 and I said, Yeah OK.  The pc did its thing and upgraded - all very smoothly with no hitches but.... Now I have no network connectivity....

I would give you the results of some commands here but I can't as this is being written on an XP m/c whilst my Ubuntu m/c lies isolated and networkless.  Sigh, at least it'll avoid viruses that way.....

So, its a wired network connected to my router/gway (192.168.0.1).
Card is a Realtek 8169SC Gigabit, identified using 
```
$lspci | grep Ethernet
```

Static IP address 192.168.04, Subnet mask 255.255.255.0.
Default gateway of 192.168.0.1.
All identifed using
```
$ifconfig
```
and
```
$netstat -nr
```

I can ping the loopback and I can ping the IP fine using
```
$ping 127.0.0.1
$ping 192.168.0.4
```

But when I try and ping the gateway
```
$ping 192.168.0.1
```

I get "Destination Host Unreachable".

If I set everything up as DHCP instead of with a static IP then the m/c fails to acquire an IP.  DHCP just confuses though, bottom line is that it should work with a static.

And, yes the cable is plugged in!!

Any help would be appreciated.


Thanks,
Andy.
P.S. I'm a total novice with Linux but should be able to follow instructions! :)

---

