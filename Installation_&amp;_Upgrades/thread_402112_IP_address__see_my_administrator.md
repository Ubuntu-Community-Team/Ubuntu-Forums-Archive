---
title: "IP address ? see my administrator?"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by EvolEcol on 2007-04-05
I am installing and cant get past the type in my IP address bit. As I dont have an administrator.... or rather I am the admin I just dont know what to do. the router for my ADL has DHCCP .. which means its automatic right?
can I just make one up?

---

### Post by qneill on 2007-04-05
I'm a ubuntu newbie but a linux old fart... I can tell you what I'd try.

First I'd expect there was a step somewhere (perhaps before the IP address dialog?) where they ask you if you should use DHCP, and then not prompt for an IP.

If not, then I'd make something up.  You should figure out what your ADL subnet is, probably 192.168.0.x or 192.168.1.x and pick an appropriate IP (192.168.x.2) which might get you up and running.

Finish your install and then worry about setting up DHCP after the installation.  I think that is in System->Administration->Network will be where to start.

The downside is that you might be offline while you figure this out.

But since you are posting on an online forum I assume you have access to the internet via some other computer?

Hope that helps,
Quentin

---

