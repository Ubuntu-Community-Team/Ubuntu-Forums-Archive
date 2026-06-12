---
title: "How to set-up internet sharing (intrepid)?"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kane77 on 2008-10-20
I have just installed Intrepid on my main desktop (home server). Everything works great, but I am not able to set up internet sharing like I was able before.

I have wlan0 wireless card that is the "source" of internet connection, eth0 the interface that I want to provide internet to. On both of those interfaces there is static IP assigned.

Before I had this script that did what I wanted to do (I ran it in rc.local:
```
#!/bin/bash
iptables --flush
iptables -t nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
iptables --table nat --append POSTROUTING --out-interface wlan0 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward

```

I tried setting up both interfaces to previous values and run this script, but it is just not working.. I can ping the other computer on the LAN (and ping my desktop from the other computer) but when I try to connect to the internet it fails. Any ideas how to make it work?

---

### Post by kane77 on 2008-10-21
It got even worse, after recently installing updates for NetworkManager it does not even show in system tray. The process is running. What I did as temporary solution I made a script that kills NetworkManager and then sets up my internet connection, but even then the network sharing does not work.

Anyone have any idea what might be the problem?

Recap:
Computer 1 wlan0 (internet): ip 192.168.18.19 /24 gw 192.168.18.1
Computer 1 eth0 (lan): ip 192.168.77.1 /24

Computer 2 eth0 ip 192.168.77.10 /24 gw 192.168.77.1

From computer 2 I am able to ping both 192.168.77.1 and 192.168.18.19, but not 192.168.18.1 (which should be the next step towards the internet)

---

