---
title: "NM 0.7 wants to be connected to ethernet and wireless simultaneously!"
date: 2008-09-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Starks on 2008-09-06
That's an improper behavior!

If I want to be on the internet, I'll do it through one medium or the other, NOT BOTH!

---

### Post by Jay_Bee on 2008-09-06
I wanted to do that once...
Use wireless to connect to internet and ethernet to share that internet connection with a computer that didn't have wireless...
But it didn't work for me.

---

### Post by Starks on 2008-09-06
> **Jay_Bee said:**
> I wanted to do that once...
Use wireless to connect to internet and ethernet to share that internet connection with a computer that didn't have wireless...
But it didn't work for me.
You can do that.

But this isn't what I'm talking about.

My laptop connects to any wireless signal it finds even if I am connected by ethernet.

---

### Post by klange on 2008-09-06
It's not an improper behavior at all. It's a standard behavior of any network management tool. Turn off your wireless. (I'll also note that every other version of NM did this)

---

### Post by MaX on 2008-09-06
If I have a cable connected then that should be the prefered mode of connection... Why else would you connect the cable?

---

### Post by Nullack on 2008-09-06
There is a range of aspects to 0.7 that are problematic. With more people helping, more things are achieved.

---

### Post by forumache on 2008-09-07
Is it interface bonding? 
[http://linux-ip.net/html/ether-bonding.html](http://linux-ip.net/html/ether-bonding.html)

Starks, do you get two IP addresses, one for each card, or only one? Could you check?

I wanted to do interface bonding, but I didn't know how. For example, I transfer something from my server through wireless and I realize that it's slow, 2.5 Mb/s so, in the middle of transfer, plug in the ethernet cable and see the speed dramatically increasing.

---

### Post by SixedUp on 2008-09-07
> **forumache said:**
> Is it interface bonding? 
[http://linux-ip.net/html/ether-bonding.html](http://linux-ip.net/html/ether-bonding.html)

Starks, do you get two IP addresses, one for each card, or only one? Could you check?

I wanted to do interface bonding, but I didn't know how. For example, I transfer something from my server through wireless and I realize that it's slow, 2.5 Mb/s so, in the middle of transfer, plug in the ethernet cable and see the speed dramatically increasing.

It's not bonding the interfaces, it's simply running two connections. It looks like it's multi-homed, though for most users both "homes" will be on the same subnet; eg:
```

sixedup@t60p:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:cf:00:3a:f9  
          inet addr:192.168.255.90  Bcast:192.168.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe00:3af9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29057 (29.0 KB)  TX bytes:7733 (7.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:15:58:2c:98:7e  
          inet addr:192.168.255.54  Bcast:192.168.255.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe2c:987e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:10321394 (10.3 MB)  TX bytes:1229600 (1.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:174700 (174.7 KB)  TX bytes:174700 (174.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CF-00-3A-F9-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sixedup@t60p:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.255.0   *               255.255.255.0   U     0      0        0 eth0
192.168.255.0   *               255.255.255.0   U     0      0        0 ath0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.255.1   0.0.0.0         UG    0      0        0 eth0

```
So, my reading of this is that any inbound traffic to my box can come over either ath0 or eth0, but my box will always respond on eth0. So, if we had a load-balancer on my network it could use the bandwidth of both those interfaces to send me traffic. But I can only use the bandwidth of one interface (eth0) to respond back. 

Clearly in this case, since eth0 is my cabled network, you'd expect me to be seeing perfectly acceptable performance, since eth0 is my default route. However, that's based on the routing table setting eth0 as the default route, and I've no idea what made that decision. However, as I plug and unplug the ethernet cable, I see the system making "sensible" decisions on what should be the default route, so one has to assume there is some intelligence in that decision :)

The problem however, is that this is only half the story. Because the system that I have locally doing DHCP & name resolution doesn't like my box asking for multiple IP addresses all associated with the same name, it only seems to remember the association for the last dhcp request. And it seems I can somehow end up in the situation where name resolution for my system ends up resolving to the wireless interface, when my default route is over the ethernet cable. Which works, but means I'm actually operating asymetrically, with inbound traffic coming over my wireless, and outbound flowing over my ethernet cable. Worse, I suspect (though haven't yet seen) that I could end up with my system operating just fine, but not resolvable by name. 

Now, its not clear yet how much of this is down to my DHCP/DNS setup (which uses Dnsmasq running on Hardy), but I bet there will be lots of other people who fall into such traps too.

Hope that helps.

---

