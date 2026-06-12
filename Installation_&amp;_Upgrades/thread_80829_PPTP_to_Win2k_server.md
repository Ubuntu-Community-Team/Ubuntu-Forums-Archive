---
title: "PPTP to Win2k server"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by Koybe on 2005-10-23
Hello,

I tried to connect via my PC to a Win2K PPTP server. I used some informations found on this forum and it seems the connection is well done.

> root@jerome:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:3E:41:A9
          inet addr:192.168.172.7  Bcast:192.168.172.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe3e:41a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6433 errors:0 dropped:0 overruns:1 frame:0
          TX packets:2875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3488292 (3.3 MiB)  TX bytes:277083 (270.5 KiB)
          Interrupt:11 Base address:0xec80

ppp0      Link encap:Point-to-Point Protocol
          inet addr:192.168.69.34  P-t-P:192.168.69.39  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:252 (252.0 b)  TX bytes:234 (234.0 b)


Then i added the route to this new network :
> root@jerome:~# route add 192.168.69.0 dev ppp0
root@jerome:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.69.0    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.69.39   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.172.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.172.1   0.0.0.0         UG    0      0        0 eth0


Put i can't get ping or connext any internal network PC. 

Thank you for any help.

---

### Post by peebee on 2005-10-23
I would guess that your gateway is incorrect.
my route -n

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
xxx.xxx.xxx.xxx  7.7.7.1         255.255.255.255 UGH   0      0        0 eth0

Yours 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.69.0    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.69.39 7.7.7.1         255.255.255.255 UGH   0      0        0 eth0

Mine is the address of the gateway at the remote site.
I think that that is what you need to add to get connectivity between the sites.

As an aside i find that pptpconfig  interface makes all this very easy.


Cheers

---

### Post by Koybe on 2005-10-23
Thank you, I'll have a look at this point.

---

### Post by peebee on 2005-10-23
no problems .. let me  know how you go.
Cheers

---

### Post by Koybe on 2005-10-23
Could you please show me your whole route table?
Just hide the ip if you want. But i can't get it work, even with pptpconfig which looks great.

---

### Post by peebee on 2005-10-23
Before VPN 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
7.7.7.0         0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         7.7.7.1         0.0.0.0         UG    0      0        0 eth0

after VPN
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.1       0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
xxx.xxx.xxx.xxx  7.7.7.1         255.255.255.255 UGH   0      0        0 eth0
7.7.7.0               0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.2.0       0.0.0.0         255.255.255.0   U     0      0        0 ppp0
0.0.0.0               7.7.7.1         0.0.0.0         UG    0      0        0 eth0

---

### Post by Koybe on 2005-10-25
Can't get any ping work, even with that same routing table. but don't worry too much, it's just for testing. I really want to do it but anyway if it's not possible.

I'd like to connect to the VPN then get to the exchange server to get mail and calendar in evolution. It would be great. If you have any informations...

Thank you anyway.

---

