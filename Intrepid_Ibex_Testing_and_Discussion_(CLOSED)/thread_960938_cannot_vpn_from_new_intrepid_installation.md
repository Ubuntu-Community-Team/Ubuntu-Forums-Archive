---
title: "cannot vpn from new intrepid installation"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by doesntcount on 2008-10-27
I've just installed intrepid and I'm trying to get my vpn connection working. I've entered all the settings but it fails to connect. /var/log/messages say:

```
Oct 27 20:46:12 brandt pppd[6615]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Oct 27 20:46:12 brandt pppd[6615]: pppd 2.4.4 started by root, uid 0
Oct 27 20:46:12 brandt pppd[6615]: Using interface ppp0
Oct 27 20:46:12 brandt pppd[6615]: Connect: ppp0 <--> /dev/pts/1
Oct 27 20:46:16 brandt pppd[6615]: LCP terminated by peer (+GHM-M^@<M-Mt^@^@^BM-3)
Oct 27 20:46:19 brandt pppd[6615]: Connection terminated.
Oct 27 20:46:19 brandt pppd[6615]: Modem hangup
Oct 27 20:46:19 brandt pppd[6615]: Exit.

```

Looks like something that the server doesn't like. Okay, perhaps I've configured something wrong. Does anybody have any idea what it could be?

As an alternative, I configured everything manually (like I have done in gentoo which works without a hitch). When I pon the connection, everything looks great:

```
Oct 27 21:07:00 brandt pppd[7886]: pppd 2.4.4 started by root, uid 0
Oct 27 21:07:00 brandt pppd[7886]: Using interface ppp0
Oct 27 21:07:00 brandt pppd[7886]: Connect: ppp0 <--> /dev/pts/2
Oct 27 21:07:01 brandt pppd[7886]: CHAP authentication succeeded
Oct 27 21:07:01 brandt pppd[7886]: MPPE 128-bit stateless compression enabled
Oct 27 21:07:03 brandt pppd[7886]: found interface eth1 for proxy arp
Oct 27 21:07:03 brandt pppd[7886]: local  IP address 192.168.21.60
Oct 27 21:07:03 brandt pppd[7886]: remote IP address 192.168.21.2
Oct 27 21:07:03 brandt pppd[7886]: primary   DNS address 192.168.16.76
Oct 27 21:07:03 brandt pppd[7886]: secondary DNS address 192.168.1.13

```

but i can't ping the remote IP, despite the route being present to tell the network how to get to the ip:

```
# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.21.2    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.0.0     0.0.0.0         255.255.0.0     U     2      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

```

If anybody can help with either of these issues, I'd really appreciate it.

Thanks.

---

