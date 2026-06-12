---
title: "upgrade to wily -- Net borked"
date: 2015-10-24
forum: Installation &amp; Upgrades
---

### Post by rpm13 on 2015-10-24
I upgraded from vivid to wily today.
Seemed to be fine during upgrade
When I reboot now i get IP as usual but both firefox and apt-get update show network is down

Network is an ADSL connection.
Also now on an old utopic laptop... so not an ISP issue it seems

---

### Post by TheFu on 2015-10-24
DNS or routing issues?

Troubleshooting: [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

---

### Post by rpm13 on 2015-10-24
> **TheFu said:**
> DNS or routing issues?

Troubleshooting: [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

Link is down?

Anyways I was exploring routing issues
Reason I ask is I suspect systemd [https://bbs.archlinux.org/viewtopic.php?id=198075](https://bbs.archlinux.org/viewtopic.php?id=198075) or some such 
though booting with upstart does not 

Note the n/a's
```

$ networkctl -a
IDX LINK             TYPE               OPERATIONAL SETUP     
  1 lo               loopback           n/a         n/a       
  2 eth0             ether              n/a         n/a       
  3 ppp0             ppp                n/a         n/a

```

Update: Troubleshooting-101 link is now working. Studying the details -- thanks

---

### Post by TheFu on 2015-10-25
The blog link should only be unavailable for about 60 seconds a day while backups are performed.  

Certain ISPs/Governments do filter it for some unknown reason.  Thailand, parts of India, Pakistan, UAE, and a few other middle-eastern countries with less-than-open governments have blocked it. I block selected subnets which have been used to attack my subnet too. Also block certain abusive referrers, iframe-abuse and abusive clients. Such is the nature of running web servers in the modern world. Sorry for any inconvenience this causes. 

I feel bad for people in China, Russia, Romania, N.Korea and anyone using Amazon for a proxy/desktop; large parts of those places are blocked. Currently, almost 7K subnets are blocked at the firewall.
```
$ sudo  iptables-save |wc  -l
6787
```

Use google-cache or  the "wayback machine" to see the content. Nothing much changes very often.  I post maybe 5 times a month. Maybe 2 posts a year are useful. ;)

---

### Post by rpm13 on 2015-10-25
> **TheFu said:**
> The blog link should only be unavailable for about 60 seconds a day while backups are performed.  


I added an update soon after saying that I got it -- so thanks

I'd say the problem is narrowed to a routing problem


Upgraded (non-working) wily
```
$ ip -d route
unicast 117.195.32.1 dev ppp0  proto kernel  scope link  src 117.195.47.122
unicast 169.254.0.0/16 dev ppp0  proto boot  scope link  metric 1000 
```
 
14.10 live booted from flash after pppoe setup. Network working
```
$ ip -d route
unicast default dev ppp0  proto boot  scope link
unicast 117.195.32.1 dev ppp0  proto kernel  scope link  src 117.195.40.157
unicast 192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.2  metric 1

```

Now what?

---

### Post by TheFu on 2015-10-25
I'm old. Don't know the details about those "new-fangled" commands.  route, ping are what I understand - as the article shows.

Sorry.

---

### Post by rpm13 on 2015-10-25
> **TheFu said:**
> I'm old. Don't know the details about those "new-fangled" commands.  route, ping are what I understand - as the article shows.

Sorry.

Heh! So am I! So extra thanks for paying attention to this.

Here are route outputs:

Bad route
```

$ route -v
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
59.93.200.1     *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 ppp0


```

Good (working) route
```
$ route -v
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         *               0.0.0.0         U     0      0        0 ppp0
117.195.48.1    *               255.255.255.255 UH    0      0        0 ppp0

```

So I guess I need a 'route add' command of some sort to make the bad more like the good?

---

### Post by TheFu on 2015-10-25
Those are extremely  different IP addresses.  Why is  that?  Is one static and old with the other being purely DHCP? Do you run a VPN?

I haven't used ppp since about 1998, so don't remember how network config works for it.
Also, check that /etc/resolv.conf has some nameservers specified. Don't edit that file.  There are other places to put DNS server IPs  -  based on how the connection is managed.  I know how  to do this for static IPs on wired ethernet, but not wifi or ppp connections. Sorry.

---

### Post by rpm13 on 2015-10-25
> **TheFu said:**
> Those are extremely  different IP addresses.  Why is  that?  Is one static and old with the other being purely DHCP? Do you run a VPN?

No Nothing fancy.
For some reason my ISP gives these two types of IPs (I think).
I checked with iplocation.net and it identifies all these with my ISP (BSNL) correctly (except of course for 192.168.1.0 which it identifies as private)

> 
I haven't used ppp since about 1998, so don't remember how network config works for it.
Also, check that /etc/resolv.conf has some nameservers specified. Don't edit that file.  There are other places to put DNS server IPs  -  based on how the connection is managed.  I know how  to do this for static IPs on wired ethernet, but not wifi or ppp connections. Sorry.

I dont think its a DNS question.
Default route is not set so effectively machine is off the net

---

