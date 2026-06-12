---
title: "PPTP-VPN and routing"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MarkusThielmann on 2010-03-27
I noticed some strange behavior when trying to connect to a VPN via PPTP.

It seems Lucid doesn't add correct routes (can't access the VPN-local network) and even after disconnecting, some routes will stay in the routing table. After a few tryouts, my routing table looks like this:

```
# sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
i59F726C3.versa fritz.box       255.255.255.255 UGH   0      0        0 eth1
i59F715B2.versa fritz.box       255.255.255.255 UGH   0      0        0 eth1
i59F715B2.versa fritz.box       255.255.255.255 UGH   0      0        0 eth1
192.168.0.1     *               255.255.255.255 UH    0      0        0 ppp0
192.168.178.0   *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         fritz.box       0.0.0.0         UG    0      0        0 eth1
```

```
#sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:c0:a8:82:e8:00  
          inet addr:192.168.178.21  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fe82:e800/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40137761 (40.1 MB)  TX bytes:5970012 (5.9 MB)
          Interrupt:18 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1304 (1.3 KB)  TX bytes:1304 (1.3 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.0.170  P-t-P:192.168.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:724 (724.0 B)  TX bytes:4247 (4.2 KB)
```

Did anyone experience similar problems? I couldn't find any related bug reports, but I don't think too much users are using PPTP (over an existing connection) anyway.

---

### Post by JCoster on 2010-03-27
If it's any help I haven't been able to connect to my VPN service since alpha 2.  I just get a timeout error...  It **very** rarely works...
Don't know if that helps (i'm not too knowledgeable on routing tables so not sure if it's related).

---

### Post by julianb on 2010-03-27
I'm running Ubuntu 10.04 Beta1. I feel like it's a significant improvement over 9.10. 

I apologize if my question seems out of place here, but I hope maybe you can answer it.

I am  confused about how to use a VPN connection in Ubuntu - It's a VPN intended for windows servers & workstations so I assume it's PPTP. 
I went to "network connections", added a vpn connection with server address (URI) and username / password.
In windows, this would be the point where there's a button you'd click that says "connect with this VPN connection" or something. In Ubuntu I can find no such button.

Also, in windows the way I would make use of the VPN is to go to the file manager and enter the address, //pym-fs1 , which would give me access to a remote filesystem. I'm not sure how I would accomplish the same thing in Ubuntu.

---

