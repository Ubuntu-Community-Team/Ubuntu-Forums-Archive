---
title: "Jaunty ipv6"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ksavich on 2009-04-14
Is it true that ipv6 is compiled into the kernel on Jaunty? Are you figgen kidding me?

---

### Post by Elfy on 2009-04-14
Apparently it is.

[http://ubuntuforums.org/showthread.php?t=1120620](http://ubuntuforums.org/showthread.php?t=1120620)

---

### Post by LowSky on 2009-04-14
Why whats the issue. IPv6 is the new standard, IPv4 is over 20 years old, and because of the world internet enabled population we need IPv6

---

### Post by ksavich on 2009-04-14
ipv6 is not a new standard. It's nowhere near standard. It wants to be, but it isn't.

---

### Post by ksavich on 2009-04-14
Correction, it is A standard - it is not THE standard.

---

### Post by binbash on 2009-04-14
I agree that it really sucks.

---

### Post by dro0g on 2009-04-14
> **LowSky said:**
> Why whats the issue. IPv6 is the new standard, IPv4 is over 20 years old, and because of the world internet enabled population we need IPv6

Begin rant:

This is nonsense, IPs are cheap as hell. If we were truly approaching a shortage, IPs would cost more. Supply/demand and all that. (This does not of course take into account the possibility of IANA doing things to distort the market.) 

I used to manage public DNS for a fairly large (30,000 employees) company. They're sitting on at least two /16s. In public DNS they had MAYBE 100 hosts listed. Figure with everything they need a few /24s at most. When we actually start running low on IPs there are plenty more companies and organizations like that that will reconsider their IP needs based on how much it's costing them or how much money they could get for IP spaces already assigned. 

The only people pushing for IPv6 are technical thugs and fearmongers. The benefits to businesses or non-geeks are zero, and the costs are awfully high. When their ISP says "that T1 will be $500 a month and the /24 to go with it will be $1000 or we can give you these snazzy IPv6 addresses for free" guess what, companies aren't going to go with the IPv6 addresses, they're going to make due with a /27 or /29. NAT is only an abomination to the purists.

I hate having to have a non-techie read me an IPv4 address, I hope to no longer be in IT when the nightmare of having someone read 2001:0db8:85a3:0000:0000:8a2e:0370:7334 across the phone comes to pass.

Just my CAO.

---

### Post by nidomedia on 2009-04-21
The IP address space problem has been fixed with internal addresses. Internet providers only have to give us an 10.x.x.x address because we don't need a public IP anyway, right?

No user needs a public IP address to get back to their home computer or host a game server or anything like that. And the ISP is the party who should decide what we can or cannot do on the network.

That's what's happening now.

And I want to log in to my machines remotely

---

### Post by cubeist on 2009-04-21
> **LowSky said:**
> Why whats the issue. IPv6 is the new standard, IPv4 is over 20 years old, and because of the world internet enabled population we need IPv6

Actually, we don't need ipv6 at all.  As any server administrator will tell you, since the advent of NAT and CIDR ipv4 has lots of life left.

Sure, ipv6 fixes a few things in regards to address portability, routing, and allocation, but it is not a perfect standard.
There is no big rush to move to ipv6; in fact, it is speculated that the only reason in the future to switch to ipv6 is if a massive amount of devices that currently don't use ip addresses started using them, Ie, embedding a permanent phone number in the ip (for voip) of every cellphone/cellphone user around the globe...

---

