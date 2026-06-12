---
title: "Ubuntu 11.10 install did not setup networking properly"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by kimbledesign on 2012-03-03
I am having a weird problem with my new Ubuntu 11.10 64 bit installation.  It looks like the ethernet adapter is connected and working but when I ping my main router at 192.168.21.1 it responds but I get a message that the wireless bridge that the Ubuntu computer is connected to at 192.168.21.6 is not responding.

This computer is setup to multi boot different operating systems and the other two operating systems work fine but I am thinking there is something wrong with the ubuntu driver for the on board ethernet of this motherboard (foxconn g33m02 rebranded for Dell).  I notice when I did an lshw command call that it is only operating at 10mb when it is a 10/100 adapter if that helps.  Also my network is not setup with DHCP it is static but I have set the DNS sever as the main router at 192.168.21.1 which worked on all the other machines that I have on this network.

I have read other posts on different sites which suggested the tests that I did below but I can't tell why this is not working because everything looks good to me other than the speed of the connection.  I have also went into my router and according to my LAN status page on the bridge router at 192.168.21.6 this computer is connected with and active connection.

Here is some info that I copied from the tests I ran.

Any help would be greatly appreciated. :)

dkimble@ubuntu:~$ sudo  lshw -class network
  
*-network               
       
description: Ethernet interface
       
product: 82562V-2 10/100 Network Connection
       
vendor: Intel Corporation
       physical id: 19
       
bus info: pci@0000:00:19.0
       logical name: eth0
       
version: 02
       serial: 00:1d:09:92:56:2c
       
size: 10Mbit/s
       capacity: 100Mbit/s
       
width: 32 bits
       clock: 33MHz
       
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       
configuration: autonegotiation=on broadcast=yes driver=e1000e 
driverversion=1.3.10-k2 duplex=full 
firmware=1.1-2 ip=192.168.21.4 
latency=0 link=yes multicast=yes 
port=twisted pair speed=10Mbit/s
       
resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)



dkimble@ubuntu:~$ ifconfig eth0
eth0      
Link encap:Ethernet  HWaddr 00:1d:09:92:56:2c  
          
inet addr:192.168.21.4  
Bcast:192.168.21.15  
Mask:255.255.255.240
          
inet6 addr: fe80::21d:9ff:fe92:562c/64 
Scope:Link
          
UP BROADCAST RUNNING MULTICAST  
MTU:1500  Metric:1
          
RX packets:774 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:267 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:124008 (124.0 KB)  TX bytes:38446 (38.4 KB)
          
Interrupt:20 Memory:fdfc0000-fdfe0000 




dkimble@ubuntu:~$ sudo apt-get install ethtool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ethtool
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 90.4 kB of archives.
After this operation, 315 kB of additional disk space will be used.
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main ethtool amd64 1:2.6.39-1
  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.92.183). - connect (101: Network is unreachable) [IP: 91.189.92.183 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_2.6.39-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_2.6.39-1_amd64.deb)  Cannot initiate the connection to us.archive.ubuntu.com:80 (91.189.92.183). - connect (101: Network is unreachable) [IP: 91.189.92.183 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
dkimble@ubuntu:~$ 

dkimble@ubuntu:~$ ping 192.168.21.1
PING 192.168.21.1 (192.168.21.1) 56(84) bytes of data.
64 bytes from 192.168.21.1: icmp_req=1 ttl=63 time=19.5 ms
64 bytes from 192.168.21.1: icmp_req=2 ttl=63 time=2.10 ms
64 bytes from 192.168.21.1: icmp_req=3 ttl=63 time=2.02 ms
64 bytes from 192.168.21.1: icmp_req=4 ttl=63 time=1.79 ms
From 192.168.21.6 icmp_seq=2 Destination Host Unreachable
From 192.168.21.6 icmp_seq=3 Destination Host Unreachable
From 192.168.21.6 icmp_seq=4 Destination Host Unreachable
64 bytes from 192.168.21.1: icmp_req=5 ttl=63 time=6.09 ms
64 bytes from 192.168.21.1: icmp_req=6 ttl=63 time=1.93 ms
64 bytes from 192.168.21.1: icmp_req=7 ttl=63 time=2.14 ms
64 bytes from 192.168.21.1: icmp_req=8 ttl=63 time=1.91 ms
From 192.168.21.6 icmp_seq=6 Destination Host Unreachable
From 192.168.21.6 icmp_seq=7 Destination Host Unreachable
From 192.168.21.6 icmp_seq=8 Destination Host Unreachable
64 bytes from 192.168.21.1: icmp_req=9 ttl=63 time=2.10 ms
64 bytes from 192.168.21.1: icmp_req=10 ttl=63 time=2.71 ms
64 bytes from 192.168.21.1: icmp_req=11 ttl=63 time=9.84 ms
64 bytes from 192.168.21.1: icmp_req=12 ttl=63 time=2.77 ms
From 192.168.21.6 icmp_seq=10 Destination Host Unreachable
From 192.168.21.6 icmp_seq=11 Destination Host Unreachable
From 192.168.21.6 icmp_seq=12 Destination Host Unreachable
^C
--- 192.168.21.1 ping statistics ---
12 packets transmitted, 12 received, +9 errors, 0% packet loss, time 11016ms
rtt min/avg/max/mdev = 1.792/4.579/19.521/5.054 ms, pipe 3
dkimble@ubuntu:~$

---

### Post by dino99 on 2012-03-03
you can try with wicd, which runs smoother vs networkmanager

sudo apt-get install wicd

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

note: of course your bridge need to be powered on and everything well plugged :)

---

### Post by kimbledesign on 2012-03-09
when I run the sudo apt-get install wicd I get a network unreachable error which I assume is because my network is not working properly and it cannot reach an external server.


Is there anyway to download this and install it without a network connection?  I booted up into my Windows 7 partition and downloaded the wicd_1.7.0+ds1.orig.tar.bz2 but when I look at the install file it mentions having dependecies that need to be installed as well so I am not sure how to make sure that all of the right files are installed correctly.

---

### Post by kimbledesign on 2012-03-16
OK,  I guess I have stumped everyone on the internet.  There are 150 people reading this post but no answers. :confused:

---

