---
title: "DHCP, NAT, ports"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-07-01
Today I have a bad day, ... sorry if I ask stupid.


I have a snom phone, which is on the LAN with the ip address 192.168.x.y and I have two servers, one is an Ubuntu server 8.04 and the other one is still a SuSE server. Both have an Ethernet connection and public IP and the internal Ethernet have the IP addresses 192.168.x.254 (Ubuntu) and 192.168.x.200 (SuSE). DHCP is supplied by Ubuntu with default gateway to Ubuntu (*254).

My desktop (192.168.x.m) can go to the Internet. So I have setup the NAT correct. BTW, where have I setup NAT?

The snom phone should connect Line 1 to the SuSE server (ok)
Interesting detail, it connects to the PUBLIC port of the SuSE server (asterisk.example.com). So it must route thru the Ubuntu server, am I right?

The remote Ubuntu server's ufw status shows:
To                         Action  From
--                         ------  ----
5060:tcp                   ALLOW   Anywhere
5060:udp                   ALLOW   Anywhere
22:tcp                     ALLOW   Anywhere
10000:udp                  ALLOW   Anywhere
10001:udp                  ALLOW   Anywhere
10002:udp                  ALLOW   Anywhere
....
5060 is the port for sip registration (there snom should connect to register)


Why the phone does not register its second line?
How can I track down this problem?

---

