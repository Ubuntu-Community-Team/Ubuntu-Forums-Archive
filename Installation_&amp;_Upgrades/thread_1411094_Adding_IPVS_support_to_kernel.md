---
title: "Adding IPVS support to kernel"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by neorush on 2010-02-19
I'm experimenting with a load balancing setup and have found some pretty good guides, but they all assume that ipvs support is built into the kernel already.  e.g. [http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster](http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster) 

So of course "modprobe ip_vs_dh" simply outputs "FATAL: Module ip_vs_dh not found."

The only downloads I can find seem to be for ipvsadm, the tool to administer linux virtual servers.  Any help / direction is greatly appreciated.

---

### Post by neorush on 2010-02-22
I never did solve this problem, however I did decide to just use the software based load balancer "balance".
[http://www.inlab.de/balance.pdf](http://www.inlab.de/balance.pdf)
Certainly not as robust as using linux virtual server, but enough for the simple load balancing / hot fail over I am attempting.  I'd love to hear any drawbacks if anyone reads this.
Link I found for the balance program was here:
[http://www.lucidtips.com/2008/08/24/setting-up-a-linux-based-software-load-balancer/](http://www.lucidtips.com/2008/08/24/setting-up-a-linux-based-software-load-balancer/)

---

### Post by rayjchris on 2010-03-30
Hey, I'm attempting to follow the same guide (I think) just got to the same point I just can't seem to find IPVS... thinking about making the load balancers under Gentoo (my distro of choice)

[http://perlstalker.amigo.net/Gentoo/LVS.phtml](http://perlstalker.amigo.net/Gentoo/LVS.phtml)

I'll report back if I get anywhere!

---

