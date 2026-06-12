---
title: "Can't Connect to Internet... Please help!"
date: 2005-10-11
forum: Installation &amp; Upgrades
---

### Post by albrad84 on 2005-10-11
I recently installed Ubuntu, but I cannot figure out how to connect to the internet, even after looking at dozens of forum posts and other documentation.  I'm very new to linux, so any help would be greatly appreciated.

[B]Basically, my network is setup as follows:
[/B]
Motorola cable modem connected to a Linksys router which is connected to another Linksys router, which is connected to my desktop.

I have 2 ethernet cards and have tried them both:
[LIST]
[*]NVIDIA nForce MCP
[*]Marvel Yukon Gigabit
[/LIST]

I have had **no problems** with the internet under windows.

In Ubuntu, I am able to type in 192.168.1.1 into the web browser and see the linksys setup page for the router that I'm directly connected to (in case this tells you anythings).

A couple months ago (before I moved) when I was first trying out Ubuntu, I had the internet working fine by plugging into an ethenet wireless adapter, so the problem can't be my ethernet card.


I had planned on trying to make the full-time switch to Linux, but if I can't get this to work soon, i may just be sticking to boring old windows...

---

### Post by grinchy on 2005-10-11
please post the output of ifconfig

try dhclient

---

### Post by albrad84 on 2005-10-11
[QUOTE=grinchy]please post the output of ifconfig

try dhclient[/QUOTE]


**[SIZE="3"]ifconfig output:[/SIZE]**
eth0      Link encap:Ethernet  HWaddr 00:11:2F:D5:D6:B5
          inet addr:192.168.1.119  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fed5:d6b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21430 (20.9 KiB)  TX bytes:2532 (2.4 KiB)
          Interrupt:22 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:11:2F:D5:F1:DB
          inet addr:192.168.1.123  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fed5:f1db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:e8000000-0

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1026594 (1002.5 KiB)  TX bytes:1026594 (1002.5 KiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          inet6 addr: ::192.168.1.119/96 Scope:Compat
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:18 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


**[SIZE="3"]dhclient output:[/SIZE]**
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth1/00:11:2f:d5:f1:db
Sending on   LPF/eth1/00:11:2f:d5:f1:db
Listening on LPF/eth0/00:11:2f:d5:d6:b5
Sending on   LPF/eth0/00:11:2f:d5:d6:b5
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.119 -- renewal in 37348 seconds.



Any ideas.....?

---

### Post by CyberBob on 2005-10-11
Your ethernet cards seem to be talking to your router OK and they have their respective IP addresses bound to them.

You may not have a DNS server configured in your network setings.  Assuming you are using the GNOME desktop ...

[LIST]
[*]click on System -> Administration ->Networking  (you'll have to re-enter your password to authenticate)

[*]click on the DNS tab

[*] If the box is empty, you need to add an address to find a DNS server. Next to the box, click "Add" and enter the IP address of your router (192.168.1.1)

[*] In the "Search Domains" box below that add the domain name of your ISP (in my case it is cinci.rr.com)
[/LIST]

This setup works for me - it seems my router just finds the correct IP of the ISP's name server and I'm off and surfing with no problems.

Good Luck.

---

### Post by albrad84 on 2005-10-13
I figured out that If I am directly connected into the first router (which is connected to the cable modem) then the internet works fine.  But if I plug it into the 2nd router, (which is plugged into the first), it does not work.

Any ideas?

---

### Post by karuptdata on 2005-10-13
Did you try what cyberbob suggested generally this fixes the problem becaus eyour getting ip addresses from router however you may just need to specify the 2 dns addresses of your ISP

---

