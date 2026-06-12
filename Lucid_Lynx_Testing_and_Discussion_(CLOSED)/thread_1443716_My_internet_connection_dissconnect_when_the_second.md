---
title: "My internet connection dissconnect when the second computer go up"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-31
when i turn on the second computer in the home network my Internet disconnect  and i need to reconnect again via sudo poff -a && sudo pon dsl-provider command the Internet share is done by this commands:

#!/bin/sh
iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m conntrack   --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j   ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward

why does this happen and how can i see a full log of my Internet connection i want to report a bug about my Internet 
connection so i need to know what package to  report i and to add full Internet log about it.

thanks in advance.

---

