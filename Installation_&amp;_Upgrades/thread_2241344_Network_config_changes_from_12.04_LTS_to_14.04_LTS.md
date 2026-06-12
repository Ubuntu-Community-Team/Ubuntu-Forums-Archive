---
title: "Network config changes from 12.04 LTS to 14.04 LTS?"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by ElToro on 2014-08-25
Has something changes in the way network connections are configured from 12.04 LTS to 14.04 LTS? 

I have just upgraded a box that I use as a proxy server with two network cards, one connecting to the LAN, the other to the WAN (via a cable modem). After upgrading to 14.04 LTS, the box does not connect on either card. That is, it seems to connect for a minute at startup (clients on the LAN are showing a connection), but then the connections are lost, both to the LAN and to the WAN. Almost looks like some service or other is initialized at startup that blocks the connections... :mad:

If I, after startup, I disable the LAN network connection on the proxy and then enable it again, the Internet is suddenly reachable on the clients. They do not reach the server, however (pinging 10.0.0.1 from a client gives 100% packet loss). At the same time, the WAN seems to be unreachable from the server...:confused: (pinging 8.8.8.8 results in 100% packet loss).

Any suggestions would be most welcome...

Ifconfig gives me the following:
```

eth0      Link encap:Ethernet  HWaddr 00:11:6b:4f:9b:a9  
          inet addr:192.168.0.201  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fe4f:9ba9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:806 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:90303 (90.3 KB)  TX bytes:104638 (104.6 KB)

eth1      Link encap:Ethernet  HWaddr 00:11:6b:4f:9b:cf  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fe4f:9bcf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:990117 (990.1 KB)  TX bytes:136964 (136.9 KB)

eth2      Link encap:Ethernet  HWaddr d4:85:64:c4:c0:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:339203 (339.2 KB)  TX bytes:339203 (339.2 KB)

```

The rc.local is as follows:
```

#!/bin/sh -e
#
# rc.local
#

    ip addr flush eth0;
    ip addr flush eth1;
    ifconfig eth0 down;
    ifconfig eth1 down;
    ifconfig lo down;
    ifconfig lo up;
    ifconfig eth0 up;
    ifconfig eth1 up;
    ifconfig eth0 192.168.0.201 netmask 255.255.255.0
    ifconfig eth1 10.0.0.1 netmask 255.255.255.0
    sysctl net/ipv4/ip_forward=0
    iptables -F
    iptables -X
    iptables -P INPUT DROP
    iptables -P OUTPUT ACCEPT
    iptables -P FORWARD ACCEPT
    iptables -t nat -F
    iptables -t nat -X
    iptables -t mangle -F
    iptables -t mangle -X
    #and on again once the policies are set
    sysctl net/ipv4/ip_forward=1
    #share on mediaserver
    #redirect port 80 on lan card and masquerade on wan card :
    iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
    #accept all packets in lo and protect against spoofing :
    iptables -A INPUT -i lo -j ACCEPT
    iptables -A OUTPUT -o lo -j ACCEPT
    iptables -A INPUT -i !lo -s 127.0.0.0/8 -j DROP
    iptables -A FORWARD -i !lo -s 127.0.0.0/8 -j DROP
    #accept only established input but all output on WAN card
    iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
    iptables -A FORWARD -i eth1 -j ACCEPT 
    iptables -A OUTPUT -o eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
    #iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT 
    #just forget the invalid packets :
    iptables -A OUTPUT -o eth0 -m state --state INVALID -j DROP
    iptables -A INPUT -i eth0 -m state --state INVALID -j DROP
exit 0

```

---

### Post by steveholt2 on 2014-10-10
Hi, 

Did you (or anyone) ever solve this? I am having a very similar problem. I recently upgraded to 14.04.1 LTS, and it no longer seems to handle my network configuration for any amount of time. I have a tuner device (I'm running Myth) connected to eth0 as a Link-Local setup, and I have a wireless card connecting to a wireless router and the internet. When I boot up, everything works fine. I can access the tuner device on the local network at a 169.254.x.x address, and I can get on the internet. However, with a day the system loses the ability to access one or both of the networks. Attempts to ping the router or the device result in "connect: Network is unreachable." Rebooting fixes everything for a few hours. This worked fine on version 12, and since I'm using this machine as a DVR, I kind of need it to be able to stay on the networks.

Anyway, this sounds like it might be the same problem, so I'm very curious if there is a resolution. Thanks.

---

