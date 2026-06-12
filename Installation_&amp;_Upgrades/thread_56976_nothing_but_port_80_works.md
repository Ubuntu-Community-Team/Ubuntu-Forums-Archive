---
title: "nothing but port 80 works"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by nodgesoft on 2005-08-14
Please excuse the newbieness but I installed Ubuntu 2 weeks ago and absolute love it. My only problem is after 2 weeks to search this forum and the internet I still cannot get any port to work except 80( web browser). Even when I try web browsing to another port it wont work. On top of this gaim wont connect to anything an no email (thunderbird or evo) will work. For some reason I got amsn to connect though.

I am not very good at iptables and I dont even know if this is the problem. I have tried with both my wireless card and ethernet card - both do exactly the same. Please help  me! Anyone got any ideas?

gecko@ubuntulaptop:~$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:0F:3D:F9:8B:60
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20f:3dff:fef9:8b60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4817 errors:200 dropped:0 overruns:0 frame:200
          TX packets:4025 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:4265889 (4.0 MiB)  TX bytes:642415 (627.3 KiB)
          Interrupt:16 Memory:e0ba0000-e0bb0000

gecko@ubuntulaptop:~$ sudo iptables --list
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by Hikaru79 on 2005-08-14
Do you have a router or very strict network firewall?

---

### Post by az on 2005-08-14
" I still cannot get any port to work except 80( web browser). Even when I try web browsing to another port it wont work"

Inbound or outbound?

Does your ISP restrict traffic?  Are you running your box from inside a university or a company and are part of their network?

---

### Post by nodgesoft on 2005-08-14
[QUOTE=Hikaru79]Do you have a router or very strict network firewall?[/QUOTE]

I am running a D-Link DSL-G604T wireless router/adsl modem running my home network.

Everything in windows works fine and I have even tried putting DMZ to my current ubuntu IP to no avail.


Any thoughts?

---

### Post by nodgesoft on 2005-08-15
Turns out it was just a router setting. Weird that my DMZ didnt fix it though.

Thanks for the help.

---

### Post by TristanMike on 2005-08-15
which router setting? in case someone has a similar problem.

---

