---
title: "Ubuntu 12.04 Server - Static IP Assignment - Waiting for network configuration"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by GAAviator on 2013-01-24
I hate to make my first post to this forum an obvious admission of stupidity on my part, but if the post helps others, then it was all worth it.

I installed a clean version of Ubuntu Server 12.04.1 LTS on a new computer.  Installation went normally.  But I needed to give this server a static IP, so I edited the /etc/network/interfaces file, deleting the following line:

iface eth0 inet dhcp

and adding the following:

iface eth0 inet static
     address 192.168.2.22
     subnet 255.255.255.0
     gateway 192.168.2.1
     dns-nameservers 22.22.22.22

When I rebooted the system it would pause for 60 seconds saying, "Waiting for Network Configuration.  It would then say, "Waiting an additional 60 seconds for Network Configuration.  Eventually the system would boot, and I could ping the gateway, but trying to ping google.com yielded "network unreachable" messages.

/etc/resolv.conf is an auto-generated file containing name servers.  When I looked at the resolv.conf file, it was empty.  Clearly something was failing during the network initialization.  Here is the problem...

In the /etc/network/interfaces file, I had the following line:

     subnet 255.255.255.0

It should have been:

     netmask 255.255.255.0

Doh...  I have been working on servers for over twenty years as an admin, but this one really bit me in the rear.  Hopefully sharing this will help someone to not burn a day on a simple mistake.

---

