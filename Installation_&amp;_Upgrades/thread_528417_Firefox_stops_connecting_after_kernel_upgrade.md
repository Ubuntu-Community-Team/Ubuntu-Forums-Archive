---
title: "Firefox stops connecting after kernel upgrade"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by victor293 on 2007-08-17
Hi, I recently upgraded Ubuntu Feisty to kernel 2.6.22-9-generic and I now cannot access the internet through my broadband connection. I should add that all was well until the upgrade. I also have a dual boot Win XP which works well (I am using it now).
I am using ADSL wired connection

I scanned through the forums (or is it fora?) for some answers to no avail, but can give this additional info:
[B]
**ping google.com** gives:
PING google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from google.com (64.233.167.99): icmp_seq=1 ttl=243 time=275 ms
64 bytes from google.com (64.233.167.99): icmp_seq=2 ttl=243 time=274 ms
....
....
--- google.com ping statistics ---
19 packets transmitted, 19 received, 0% packet loss, time 17996ms
rtt min/avg/max/mdev = 226.629/268.537/275.674/14.312 ms

**ping 64.233.183.103** gives:
PING 64.233.183.103 (64.233.183.103) 56(84) bytes of data.
64 bytes from 64.233.183.103: icmp_seq=1 ttl=233 time=400 ms
64 bytes from 64.233.183.103: icmp_seq=2 ttl=233 time=403 ms
......
......
--- 64.233.183.103 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 7994ms
rtt min/avg/max/mdev = 400.016/402.177/403.593/1.358 ms

sudo cat resolv.conf[/B] produces:  nameserver 192.168.1.254

and the following commands produce:

victor@victor-desktop:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:00:21:03:05:C4  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:21ff:fe03:5c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7754 (7.5 KiB)  TX bytes:10473 (10.2 KiB)
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

victor@victor-desktop:~$** sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:00:21:03:05:c4
Sending on   LPF/eth0/00:00:21:03:05:c4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.100 -- renewal in 242368 seconds.

Can anybody figure out why all the pings work but Firefox (and the old Mozilla which I also have installed) do not work?

Note also that rebooting to the older kernel does not help, it would appear some config files have changed.

Any assistance would be geatly appreciated.
Victor

---

