---
title: "problem with apt-get update"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by Ag_Liz on 2015-02-28
hi there everyone,

I am experienceing a rather strange situation on an lubuntu server and not sure how to solve this issue. when i am  trying to apt-get update i get this : 

> Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease

Err [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease

Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease

Err [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg
  Could not resolve 'archive.canonical.com'
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release.gpg
  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty/InRelease)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/trusty/InRelease](http://archive.canonical.com/ubuntu/dists/trusty/InRelease)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease](http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease)

W: Failed to fetch [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/dists/trusty/InRelease](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/dists/trusty/InRelease)

W: Failed to fetch [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/dists/trusty/Release.gpg](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/trusty/Release.gpg](http://archive.canonical.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.



i read some threads like this : [http://ubuntuforums.org/showthread.php?t=2243846](http://ubuntuforums.org/showthread.php?t=2243846) and some more 



 When i 
[HTML]ping google.com[/HTML] i get : [HTML]ping: unknown host google.com[/HTML]
i realized that i can not ping to [www.example.com]("http://www.example.com") domain but  if i get the ip of the page the ping is working ok!  


So i am geusing this has  something to do with the translation of domains to ip' s ? How do i check something like this ? 
where do i start?

tryied this: [http://ubuntuforums.org/showthread.php?t=2103035](http://ubuntuforums.org/showthread.php?t=2103035)
and this : [http://askubuntu.com/questions/465729/ping-unknown-host-google-com-in-ubuntu-server](http://askubuntu.com/questions/465729/ping-unknown-host-google-com-in-ubuntu-server)
with no luck!

I am working through SSl terminal. When i notice this problem i went to the server and through the browser i could not connect to the internet. No internet connection. 
 
From outside the local net i can acces the page serving an iframe from youtube.......:lolflag:   since if the problem is that it canot translate the domains !!!

thanks in advance!

---

### Post by TheFu on 2015-02-28
Looks like a DNS issue.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has steps to determine if that really is the issue. Start from the top, work through and post the results back here - copy/paste please and use "code tags" in the Adv Reply so it is easier to read the output.

---

### Post by Ag_Liz on 2015-02-28
I did it heres the result :

[HTML]ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.361 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.374 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=0.369 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=0.372 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=0.363 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=0.389 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=0.371 ms
64 bytes from 192.168.2.1: icmp_seq=8 ttl=64 time=0.357 ms
64 bytes from 192.168.2.1: icmp_seq=9 ttl=64 time=0.358 ms
64 bytes from 192.168.2.1: icmp_seq=10 ttl=64 time=0.377 ms
64 bytes from 192.168.2.1: icmp_seq=11 ttl=64 time=0.364 ms
^C

[/HTML]

[HTML] ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=30.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=30.9 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=30.9 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=57 time=30.6 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=57 time=30.1 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=57 time=35.1 ms
^C

[/HTML]


[HTML]
 ping google.com

ping: unknown host google.com
[/HTML]


[HTML]
dmesg |grep eth[0-9]

[    2.070405] uli526x 0000:00:1b.0 eth0: ULi M5263 at pci0000:00:1b.0, 00:40:d0:82:1e:2f, irq 20
[   23.335062] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.660740] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.661724] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   50.664392] uli526x 0000:00:1b.0 eth0: NIC Link is Up 100 Mbps Full duplex
[   50.664447] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[178698.796878] uli526x 0000:00:1b.0 eth0: NIC Link is Down
[178700.796375] uli526x 0000:00:1b.0 eth0: NIC Link is Up 100 Mbps Full duplex
[186307.796679] uli526x 0000:00:1b.0 eth0: NIC Link is Down
[186312.002265] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[186313.796395] uli526x 0000:00:1b.0 eth0: NIC Link is Up 100 Mbps Full duplex
[186313.796446] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

[/HTML]


[HTML] 

sudo lshw -C network

*-network:1
       description: Ethernet interface
       product: ULi 1689,1573 integrated ethernet.
       vendor: ULi Electronics Inc.
       physical id: 1b
       bus info: pci@0000:00:1b.0
       logical name: eth0
       version: 50
       serial: 00:40:d0:82:1e:2f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=uli526x driverversion=0.9.3 duplex=full ip=192.168.2.80 latency=128 link=yes maxlatency=40 mingnt=20 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 ioport:e000(size=256) memory:d000a000-d000a0ff


[/HTML]

[HTML]
ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:40:d0:82:1e:2f
          inet addr:192.168.2.80  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe82:1e2f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:957452 errors:0 dropped:3354 overruns:0 frame:0
          TX packets:855888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:295125518 (295.1 MB)  TX bytes:225281617 (225.2 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:789520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:789520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:62708798 (62.7 MB)  TX bytes:62708798 (62.7 MB)

wlan0     Link encap:Ethernet  HWaddr 00:10:60:61:53:01
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[/HTML]



[HTML]

~$ more /etc/resolv.conf

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

[/HTML]


[HTML]
route

.Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     *               255.255.255.0   U     1      0        0 eth0


[/HTML]

---

### Post by Ag_Liz on 2015-02-28
On the 
[HTML]
dmesg |grep eth[0-9]

eth0: link is not ready
[/HTML]
what does it stand for ? i think something is wrong there

---

### Post by TheFu on 2015-02-28
It means the network wasn't up the first time, then came up later (which is normal) but I see everything except DNS is working.

You have a DNS issue, so that is what you need to troubleshoot. Check your DNS settings - perhaps try a public, trusted DNS, not the one from your ISP?  ISPs have been known to have DNS issues - for years, it was a forgotten box, far in their data center corner that nobody knew about. Around 2005, pretty much every ISP upgraded their DNS from the 1990 SunOS box previously there. ;)

There are lots of DNS servers to choose - openDNS isn't bad, fine for troubleshooting.  Also, some ISPs block all outbound DNS and redirect it calling is a "security feature", which is sorta true for Windows PCs. Use dig, nslookup and host to see where your DNS is pointed.

BTW, if the router provides DNS on your network, try rebooting it, then restarting the networking on your ubuntu machine. There are lots of ugly attacks against home routers with default settings or the stock firmware running - so if something seems funny, it is worth doing a little more research.  For a few years, attacks using javascript from the client PC running inside the LAN have been used against routers. [Router Security Checklist]("http://blog.jdpfu.com/pages/wifi-security")

---

### Post by Ag_Liz on 2015-02-28
Thanks **[COLOR=#000000]TheFu[/COLOR]**  for your help i just changed the dns and worked fine! I wonder why i didn't look that way before!! thanks again!

but i have a question, maybe a cilly one though, is there a reason that this issue poped up now because i never had this problem almost a year now that i am using this machine, 
and also why the other pc don't have the same problems  on the same network ? ?

---

### Post by TheFu on 2015-02-28
> **Ag_Liz said:**
> but i have a question, maybe a cilly one though, is there a reason that this issue poped up now because i never had this problem almost a year now that i am using this machine, 
and also why the other pc don't have the same problems  on the same network ? ?

I have no idea - if you reboot the other machine and it breaks too - then I'd check the router.

---

### Post by Ag_Liz on 2015-02-28
Will do thank you for all your help

---

