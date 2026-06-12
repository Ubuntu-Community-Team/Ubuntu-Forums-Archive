---
title: "Newbie with ambitious plan"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by Haridimos on 2011-07-17
Hi guys,

the next days i'm going to have an internet connection to my house. I'm thinking of using an old Pentium 2/333MHz as gateway/firewall.
The following image shows shat i have in my mind.

[U][[IMG]http://img807.imageshack.us/img807/7291/ubuntu2.th.jpg[/IMG]]("http://img807.imageshack.us/i/ubuntu2.jpg/")
[/U]

Fisrtly a terminal device is given by the ISP in order to connect. The Pentium 2 serves as a gateway. The laptop and the desktop PC are my machines.

I'm planning to use also a wireless device in order to supply free internet connection to my neighbors. In order to do this i need the following.

To isolate the wireless device from the home network
To apply a bandwidth policy: i'm the one who pays, i should control the bit rate allocation
To have a log of the wireless device's connections

Is it possible using a Pentium 2/333MHz running Ubuntu?

---

### Post by oldos2er on 2011-07-17
> **Haridimos said:**
> Is it possible using a Pentium 2/333MHz running Ubuntu?

It would be painfully slow, if it worked at all. Check Ubuntu's system requirements.

Why not use one of the distros made to function as a firewall? 
[http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions)

---

### Post by 1clue on 2011-07-17
Better yet, go get a wireless router with hardware connections off of ebay and install dd-wrt on it.

PC hardware is pretty slow as a router IMO.  That box is marginal IMO.

While I can't say I like the rate at which dd-wrt improves, it IS a linux distribution for a wireless router, and it handles pretty much anything the kernel handles.

---

### Post by Cheesehead on 2011-07-17
It can be done, though the amount of effort may not be worthwhile for a paying concern.

1) The 'terminal device' from your ISP may not be neccessary. Depends upon what it does. For example, when I built my own router/gateway device, I used my own PCI DSL modem instead of the ISP-provided DSL modem.

2) I found it VERY helpful to set up the whole router/gateway device in a VM and test it a bunch before installing onto hardware. Inclusing testing the install procedures. Rolling back an error in VM is much easier!

3) Isolating the wireless network seems simple enough - leave it as a separate subnet (don't bridge it to the eth LAN).

4) Logging wireless connections is simple enough, but depends on what you mean. If you mean 'Each time a wireless device connects/disconnects from the wireless network', dnsmasq already does that - just grep the log. Alternately, dnsmasq will also run a shell script of your choosing each time a connection/disconnection occurs. If, instead, you mean tracking wireless device internet usage, then use iptables' built-in logging.

---

