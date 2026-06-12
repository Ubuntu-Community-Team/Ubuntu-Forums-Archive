---
title: "Network setup for 2 nics, Home Media Player"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by Wesw94 on 2012-03-13
Background
-new to Ubuntu (latest Mythbuntu rel 11.10 32 bit)
-some old Linux exposure

Purpose
-Media Server (part of plan to get rid of cable-tv $85/mo)
-2 Nics (keep media data streams on own hi-bandwidth clean LAN)
-1st nic dhcpc to home router (wireless-n+4LAN+WAN-CableModem $24)
-2nd nic to moca net using existing home cable wiring
  (want static ip, dhcp server, caching local dns perhaps)

Problem
IMHO the above config should be common enough to be the/a default if 2 nics found on install. After trying stuff and searching I do not yet have a good working setup.  I could not get stock Network Manager to do it.  

Then I added the following to /etc/network/interfaces  
(eth0 ends up as nic 2 to the media LAN)
  
```

auto eth0
iface eth0 inet static
        address 192.168.40.1
        netmask 255.255.155.0

```

when I run ifup eth0 I get

[code]
wes@mediaServer1:~$ sudo ifup eth0
[sudo] password for wes: 
Error: an inet prefix is expected rather than "192.168.40.1/255.255.155.0".
Failed to bring up eth0.
[code]

This seems to be an often reported bug in the ifupdown package
but.....

I will keep trying stuff but there should be a proper (supported) and easy way to get this working. If so I'll help doc it for us 
newbies.

Wes

---

### Post by cfabbriumd on 2012-05-19
You probably already noticed this already, but you have an invalid subnet mask

```

auto eth0
iface eth0 inet static
        address 192.168.40.1
        netmask 255.255.**155**.0

```

You should change this to:

```

auto eth0
iface eth0 inet static
        address 192.168.40.1
        netmask 255.255.**255**.0

```

I made the same mistake, and I was wondering why the "an inet prefix is expected rather than" was coming up. Your question answered mine.

---

