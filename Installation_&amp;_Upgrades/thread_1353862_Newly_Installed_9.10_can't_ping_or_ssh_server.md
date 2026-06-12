---
title: "Newly Installed 9.10 can't ping or ssh server"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by jfrek on 2009-12-13
I'm new to linux and ubuntu. I have just installed Ubuntu server 9.10 on my old Dell computer.  When I try to ping or ssh to the computer the connection times out.  During installing,  the automatic DHCP process didn't work so I did a manual network setup.  During the setup I used the ip addresses from my other computer on the same LAN so i believe they are right.  I can use ssh localhost and ssh 192.168.1.104 on the ubuntu server but I can't even ping from other computers on my LAN.  Any Ideas?

---

### Post by darkod on 2009-12-13
> **jfrek said:**
> I'm new to linux and ubuntu. I have just installed Ubuntu server 9.10 on my old Dell computer.  When I try to ping or ssh to the computer the connection times out.  During installing,  the automatic DHCP process didn't work so I did a manual network setup.  During the setup I used the ip addresses from my other computer on the same LAN so i believe they are right.  I can use ssh localhost and ssh 192.168.1.104 on the ubuntu server but I can't even ping from other computers on my LAN.  Any Ideas?

When you say you used the ip address from other computer, you did change the last number right? Two computers with same ip can't exist on the same network.
I am not familiar with ubuntu server, but it might have some kind of firewall enabled by default which would not return the pings you are trying.

---

