---
title: "Issue with networking.service after migration from 14.04 to 16.04"
date: 2017-03-31
forum: Installation &amp; Upgrades
---

### Post by Shadow aok on 2017-03-31
Hello,

We upgraded one of our ubuntu server from 14.04 AMD64 to 16.04 AMD64.
It is an EG-32 dedicated server at OVH.
It went well, but we have an issue with networking.service, although networks works fine :

```
root:/etc/udev/rules.d# systemctl status networking.service 
&#9679; networking.service - Raise network interfaces 
   Loaded: loaded (/lib/systemd/system/networking.service; enabled;  vendor preset: enabled) 
  Drop-In: /run/systemd/generator/networking.service.d 
           &#9492;&#9472;50-insserv.conf-$network.conf 
   Active: failed (Result: exit-code) since Thu 2017-03-30 11:09:01  CEST; 1h 13min ago 
     Docs: man:interfaces(5) 
 Main PID: 1002 (code=exited, status=1/FAILURE) 


Mar 30 11:08:52 bjo-stor-001.prod.bajoo.fr ifup[1002]: RTNETLINK  answers: File exists 
Mar 30 11:08:52 bjo-stor-001.prod.bajoo.fr ifup[1002]: /sbin/ifup:  waiting for lock on /run/network/ifstate.eth0 
Mar 30 11:08:56 bjo-stor-001.prod.bajoo.fr ifup[1002]: RTNETLINK  answers: File exists 
Mar 30 11:08:56 bjo-stor-001.prod.bajoo.fr ifup[1002]: Failed to bring  up eth0. 
Mar 30 11:09:01 bjo-stor-001.prod.bajoo.fr ifup[1002]: RTNETLINK  answers: File exists 
Mar 30 11:09:01 bjo-stor-001.prod.bajoo.fr ifup[1002]: RTNETLINK  answers: File exists 
Mar 30 11:09:01 bjo-stor-001.prod.bajoo.fr systemd[1]:  networking.service: Main process exited, code=exited, status=1/FAILURE 
Mar 30 11:09:01 bjo-stor-001.prod.bajoo.fr systemd[1]: Failed to start  Raise network interfaces. 
Mar 30 11:09:01 bjo-stor-001.prod.bajoo.fr systemd[1]:  networking.service: Unit entered failed state. 
Mar 30 11:09:01 bjo-stor-001.prod.bajoo.fr systemd[1]:  networking.service: Failed with result 'exit-code'.
```

Network still works fine but ipv6 seems kind of slow to respond (15s to have the first answer from ping6).

```
oot:/etc/udev/rules.d# traceroute6 ipv6.google.com 
traceroute to ipv6.l.google.com (2a00:1450:4007:80a::200e) from  2001:41d0:2:ac97::, 30 hops max, 24 byte packets 
 1  vss-6b-6k.fr.eu (2001:41d0:2:acff:ff:ff:ff:fd)  1037.64 ms 1.16 ms   0.903 ms 
 2  2001:41d0:0:5:3::1a4 (2001:41d0:0:5:3::1a4)  0.275 ms  0.24 ms   0.119 ms 
 3  2001:41d0:0:5:2::30 (2001:41d0:0:5:2::30)  0.377 ms  0.402 ms 0.204 ms 
 4  * 2001:41d0::10fe (2001:41d0::10fe)  2.082 ms * 
 5  be99-1044.gsw-1-a9.fr.eu (2001:41d0::c71)  4.02 ms  4.058 ms 4.002 ms 
 6  google.as15169.fr.eu (2001:41d0::171)  3.978 ms  4.111 ms 3.899 ms 
 7  2001:4860:0:1017::1 (2001:4860:0:1017::1)  4.293 ms  4.272 ms 4.141 ms 
 8  2001:4860:0:1::1e37 (2001:4860:0:1::1e37)  4.281 ms  4.223 ms 4.124 ms 
 9  par10s28-in-x0e.1e100.net (2a00:1450:4007:80a::200e)  4.053 ms   4.096 ms  4.097 ms 


root@:/etc/udev/rules.d# ping6 ipv6.google.com 
PING ipv6.google.com(par10s28-in-x0e.1e100.net) 56 data bytes 
64 bytes from par10s28-in-x0e.1e100.net: icmp_seq=1 ttl=54 time=4.24 ms 
64 bytes from par10s28-in-x0e.1e100.net: icmp_seq=2 ttl=54 time=4.28 ms 
64 bytes from par10s28-in-x0e.1e100.net: icmp_seq=3 ttl=54 time=4.29 ms 
64 bytes from par10s28-in-x0e.1e100.net: icmp_seq=4 ttl=54 time=4.25 ms 
64 bytes from par10s28-in-x0e.1e100.net: icmp_seq=5 ttl=54 time=4.40 ms 
64 bytes from par10s28-in-x0e.1e100.net: icmp_seq=6 ttl=54 time=4.26 ms 
^C64 bytes from ip6-allhosts: icmp_seq=7 ttl=54 time=4.27 ms 

--- ipv6.google.com ping statistics --- 
7 packets transmitted, 7 received, 0% packet loss, time 30048ms 
rtt min/avg/max/mdev = 4.241/4.288/4.403/0.099 ms 


# route -6 
Kernel IPv6 routing table 
Destination                    Next Hop                   Flag Met Ref  Use If 
2001:41d0:2:ac97::/64          ::                         U    256 0      0 eth0 
2001:41d0:2:acff:ff:ff:ff:ff/128 ::                         U 1024 0      5 eth0 
fe80::/64                      ::                         U    256 0      0 eth1 
fe80::/64                      ::                         U    256 0      0 eth1.100 
fe80::/64                      ::                         U    256 0      0 eth0 
::/0                           2001:41d0:2:acff:ff:ff:ff:ff UG 1024  1     0 eth0 
::/0                           ::                         !n   -1 1   221 lo 
::1/128                        ::                         Un   0 1  1902 lo 
2001:41d0:2:ac97::/128         ::                         Un   0 1   134 lo 
fe80::ec4:7aff:fe6c:98f0/128   ::                         Un   0 1     9 lo 
fe80::ec4:7aff:fe6c:98f1/128   ::                         Un   0 1     4 lo 
fe80::ec4:7aff:fe6c:98f1/128   ::                         Un   0 1     0 lo 
ff00::/8                       ::                         U    256 0      0 eth1 
ff00::/8                       ::                         U    256 0      0 eth1.100 
ff00::/8                       ::                         U    256 1      0 eth0 
::/0                           ::                         !n   -1 1   221 lo
```

eth0 is the wan link and eth1 the lan one (vrack).
Both of them works just fine.
ifconfig -a reports the same names for our interfaces (eth0, eth1 and eth1.100)

If we try to ifup eth0 (although it is already up and working) :
```
root:/var/log# ifup -v eth0 
Configuring interface eth0=eth0 (inet) 
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d 
run-parts: executing /etc/network/if-pre-up.d/ethtool 
run-parts: executing /etc/network/if-pre-up.d/vlan 
/bin/ip addr add 176.31.235.X/255.255.255.0 broadcast 176.31.235.255     dev eth0 label eth0 
RTNETLINK answers: File exists 
Failed to bring up eth0.
```

Here's our network interfaces :
```
auto lo 
iface lo inet loopback 

auto eth0 
iface eth0 inet static 
        address 176.31.235.X 
        netmask 255.255.255.0 
        network 176.31.235.0 
        broadcast 176.31.235.255 
        gateway 176.31.235.254 

iface eth0 inet6 static 
        address 2001:41D0:2:AC97:: 
        netmask 64 
        post-up /sbin/ip -family inet6 route add  2001:41D0:2:ACff:ff:ff:ff:ff dev eth0 
        post-up /sbin/ip -family inet6 route add default via  2001:41D0:2:ACff:ff:ff:ff:ff 
        pre-down /sbin/ip -family inet6 route del default via  2001:41D0:2:ACff:ff:ff:ff:ff 
        pre-down /sbin/ip -family inet6 route del  2001:41D0:2:ACff:ff:ff:ff:ff dev eth0 

auto eth1 
iface eth1 inet static 
        address 172.16.100.1 
        netmask 255.255.0.0 
        network 172.16.0.0 
        broadcast 172.16.255.255 

auto eth1.100 
iface eth1.100 inet static 
        address 10.0.0.1 
        netmask 255.255.255.0 
        vlan-raw-device eth1
```

Any idea ?
Thanks.

---

### Post by Shadow aok on 2017-04-03
I saw some solutions with udev, but it is already in place :
```
# ll /etc/udev/rules.d
total 16K
drwxr-xr-x 2 root root 4.0K Apr  3 17:09 .
drwxr-xr-x 4 root root 4.0K Mar 30 10:59 ..
-rw-r--r-- 1 root root  623 Oct 28  2015 70-persistent-net.rules
lrwxrwxrwx 1 root root    9 Oct 28  2015 80-net-name-slot.rules -> /dev/null
lrwxrwxrwx 1 root root    9 Oct 28  2015 80-net-setup-link.rules -> /dev/null
-rw-r--r-- 1 root root   51 Oct 28  2015 99-dev_root.rules
```

* 70-persistent-net.rules
```
# PCI device 0x8086:0x1521 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="0c:c4:7a:6c:98:f1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x1521 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="0c:c4:7a:6c:98:f0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

---

