---
title: "can't access computers on subnet but can get to internet?"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by jsprenkl on 2010-06-16
Good evening,
I've just installed an ubuntu 10.04 lts system. It's working very well with one exception. I can get to the internet but cannot access any other machines on my local network!

I can ping the gateway but no other machines:

ping 10.0.0.1
```
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=64 time=1.02 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=0.622 ms

```

ping 10.0.0.5
```
PING 10.0.0.5 (10.0.0.5) 56(84) bytes of data.
From 10.0.0.8 icmp_seq=1 Destination Host Unreachable
From 10.0.0.8 icmp_seq=2 Destination Host Unreachable
From 10.0.0.8 icmp_seq=3 Destination Host Unreachable
```

I shouldn't be getting Destination unreachable here.

Here's the output from everything I could think of that might help:

ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:51:07:b2  
          inet addr:10.0.0.8  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe51:7b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:222584 (222.5 KB)  TX bytes:47020 (47.0 KB)
          Interrupt:29 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.186.1  Bcast:172.16.186.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.86.1  Bcast:172.16.86.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

eth0 is supposed to be a static ip address at 10.0.0.8. The vmnet* interfaces were added by vmware player.

route -n

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.86.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
172.16.186.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 eth0
```

sudo iptables --list
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

I tried using the network connections program to setup the network but it did not work and tells me the connection has never been accessed. The network status notification icon in the task bar has disappeared.

I tried entering in the configuration manually:

more /etc/network/interfaces 
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.8
gateway 10.0.0.1
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
```

Any suggestions? Could vmware have borked it?

Thanks

---

### Post by darkod on 2010-06-16
Any firewalls on the other computers blocking you to see them? Not sure if that can block ping though.

---

### Post by lechien73 on 2010-06-16
What is the subnet mask on the other computers? Is it 255.255.255.0 as well?

---

### Post by jsprenkl on 2010-06-17
I've solved the issue. The SSH and ping packages incorrectly present the message "no route to host" when the host is not present. After fixing a hardware issue I now have it working.

Thanks to all who tried to help

---

