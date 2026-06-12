---
title: "Can't get ny network online"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by Svartvit on 2005-07-28
Hi!
Decided to go Linux yet again, so I assigned 30 Gig to Windows XP and 200 to Ubuntu in a dual boot. Everything went smooth during the install, but when I thought I was ready to go, all hell broke loose. Oh the humanity. I couldn't access the Internet.

Basically, I've got a static IP and a paper from my ISP with all the information I need to configure the internets. DNS servers, Netmask (255.255.255.192), IP address and a gateway which is the same as my IP. Everytime I check ny networks config in GNOME or in interfaces.conf, it seems awfully correct in my eyes, but still, whenever I try to access a http address, it just stops at the host resolving process, and I don't know frickin why.

And don't be fooled, I'm not your average newbie, I'm just a complete and utter retard when it comes to networking. ](*,) 

If anyone's got a clue, let me know, and if you need more details, just ask. All help is appreciated.

*edit*
And yeah, I connect via this black box in the living room. I just realized I don't know if it's a built-in router-modem all-in-one or not. Does it make a difference, I'm the only one connected to it?

I'm also a total rookie to this forum, and might have misplaced this thread. Bare with me.

---

### Post by amohanty on 2005-07-29
1. Try to check and configure it again via:
Applications->System Tools->Network Tools

2. Post result of:
>>  ifconfig

3. Post /etc/hosts
4. Post /etc/resolv.conf

---

### Post by heimo on 2005-07-29
Hi!

[QUOTE=Svartvit]
Basically, I've got a static IP and a paper from my ISP with all the information I need to configure the internets. DNS servers, Netmask (255.255.255.192), IP address and a gateway which is the same as my IP. [/QUOTE]

This sounds weird. You computers IP address and gateways IP address need to be different (most probably, I can imagine a scenario where it could be same, but it's highly unlikely).

What happens if you ping localhost (ip) or gateway? That "black box" can be either a router or a bridge. If it's router, it has its own IP address (and it probably acts as a gateway), if it's bridge, it's "transparent" and next hop (next router) is on ISPs side.

BTW, that subnet mask is quite "large", 5-bits if I'm not mistaken, for ~32 addresses, which is a lot for a household. I don't doubt this information, but just as an observation - it could be a subnet for a small company.

---

### Post by bored2k on 2005-07-29
[QUOTE=heimo]This sounds weird. You computers IP address and gateways IP address need to be different (most probably, I can imagine a scenario where it could be same, but it's highly unlikely).[/QUOTE]
I agree. That's most likely the problem. You can't have 10.0.0.1 as both gateway and IP address (an example).

---

### Post by Svartvit on 2005-07-29
[QUOTE=amohanty]2. Post result of:
>>  ifconfig[/quote]
```
eth0        Link encap:Ethernet  HWaddr 00:10:48:3D:D2:13
            inet addr:83.227.160.163  Bcast:83.227.160.191  Mask:255.255.255.192
            inet6 addr: fe80::210:4bff:fe3D:d213/64 Scope: Link
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:29 errors:0 dropped:0 overruns:0 carrier:29
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 b)  TX bytes: 1818 (1.7 KiB)
            Interrupt:11 Base address:0xc00

lo          (bunch of stuff)
```

> 3. Post /etc/hosts
```
127.0.0.1 localhost.localdomain localhost failsafe
83.227.160.163 failsafe

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6 allrouters
ff02::3 ip6 allhosts
```

> 4. Post /etc/resolv.conf
```
nameserver 195.54.122.200
```

[QUOTE=heimo]This sounds weird. You computers IP address and gateways IP address need to be different (most probably, I can imagine a scenario where it could be same, but it's highly unlikely).[/quote]
I've got papers that tells me to configure my gateway with my IP, and as I write this, I use that very configuration in Windows XP.

> What happens if you ping localhost (ip) or gateway?
The packages seems to be delivered accordingly.

---

### Post by Svartvit on 2005-07-29
Hi!
It seems as if it all worked out at last. I don't have a god damn clue about what was wrong, I booted Ubuntu just now and without me having configured anything since the last time, I suddenly was in the loop again. It's almost scary, but hey, it's Linux. \\:D/ 

Thanks for the help anyway. Appreciate it.

---

### Post by amohanty on 2005-07-30
> I've got papers that tells me to configure my gateway with my IP, and as I write this, I use that very configuration in Windows XP. 

Typically your gateway would be your router. If your DSL modem is also a router (doesnt appear to be since your IP addy is not of the form:
192.168.... or a bunch of various intranet apps) then it should also have an IP address that you can use as gateway. Usually when you have direct connection to the internet without using a router your gateway IP is that of a 'WAN Router' something your ISP uses, which WILL be different from your IP.

Now that its working I suggest that you do another ifconfig and compare it to the one you got when you could not connect. Linux is quite unlike voodoo however much people would like to believe so, if it does not do something, it doesnt do it for a reason, and getting to the root always helps in the long run...

AM

---

### Post by heimo on 2005-07-30
I second amohanty. Of course, for most people it's enough that it works, but it definitely helps to find out why it works and what the current settings are. I'd check *route -n *and *ifconfig eth0* and do some tracepaths to find my exact network setup / topology, maybe even write down some notes so it's easier to setup / debug next time. I really, really doubt that the computers IP and gateways IP would be same... It's not.

---

