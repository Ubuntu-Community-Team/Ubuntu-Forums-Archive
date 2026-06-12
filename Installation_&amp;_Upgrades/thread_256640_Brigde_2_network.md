---
title: "Brigde 2 network"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by cyberjojo on 2006-09-13
I got a complex question. 

I wanna setup a fw/router/gw on a server. It got 3 nic's.

This is what i want it to do:

eth0 = wan
eth1 = lan 192.168.0.0
eth2 = lan 192.168.2.0

eth1 will access internet via eth0 

eth2 will serve neighbours lan to connect to services on my lan e.g samba, ftp, irc, etc... 

Im guessing i have to bridge eth1 and eth2, but how?
Hoping someone can help me with this... :)

-Cyberjojo

---

### Post by Original Brownster on 2006-09-13
Hi,
Not sure what you mean by a bridge but I think I can help you.

> **cyberjojo said:**
> 
This is what i want it to do:

eth0 = wan
eth1 = lan 192.168.0.0
eth2 = lan 192.168.2.0

eth1 will access internet via eth0 

eth2 will serve neighbours lan to connect to services on my lan e.g samba, ftp, irc, etc... 
-Cyberjojo

So eth1 will attach to your pc/network and eth2 to your neighbours pc/network.
All you need on the server is a default gw set to eth0 (I assume you have a broadband modem attached to this via rj45)
A routing entry for 192.168.0.0 to route through eth1
A routing entry for 192.168.2.0 to route through eth2

Traffic from your neighbour arriving on eth2 with address in range 192.168.0.x will route to your network via eth1, anything else will go default gw and wan.

Equally traffic from your net goes to eth1 where if in neighbours range goes via eth2 else to the wan.

routing entries can be added temporarily whilst you mess around 'man route'
once you have it working they can be made permanent.

you can experiment by creating temporary routes example:

$ route add -net 192.168.0.0 netmask 255.255.255.0 dev eth1

this creates a route so the ubunto box sends all traffic destined for the lan to your eth1 card and out onto your lan where hopefully one of your pc's will receive it.

$ route add default gw dev eth0

send anything else through eth0 (you've connected to your cisco router)

useful commands:

check the routing table with:
$ netstat -rn

interface config with:
$ifconfig -a

once your happy with the routing entries, make the permanent by creating a file as below (cut from someone elses post)

Create that file /etc/network/if-up.d/static-routes as follow
#!/bin/sh
# Set static routes
#
/sbin/route add -net foo bar
/sbin/route add -net foo bar

---

