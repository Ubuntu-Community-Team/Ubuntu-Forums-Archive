---
title: "[SOLVED] No network after upgrading Gutsy-&amp;gt;Hardy"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by benbelly on 2008-06-03
I just upgraded my desktop from Gutsy to Hardy, and I can no longer access the network.  I looked at 
[http://ubuntuforums.org/showthread.php?t=807563](http://ubuntuforums.org/showthread.php?t=807563)
[http://ubuntuforums.org/showthread.php?t=807020](http://ubuntuforums.org/showthread.php?t=807020)

But they didn't help. I saw a suggestion elsewhere to do:

sudo lshw -C network

which I tried, and I get nothing.

I don't know if this is related or not, but I get warnings in the panel about a program crashing; however, when I click on that, I get a "Starting Administration" box on my taskbar for about ten seconds, then it disappears.  The same thing happens when I try to run Hardware Drivers, or Hardware Test.

Any thoughts on what to try?

Thanks
-Ben

---

### Post by benbelly on 2008-06-03
Not to beat a dead horse, but I'm really stuck on this!
Here are the results of ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:1a:92:7d:52:53  
          inet addr:192.168.1.201  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe7d:5253/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:19192 (18.7 KB)
          Interrupt:248 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:7d:69:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:247 Base address:0xe000 

eth1:avahi Link encap:Ethernet  HWaddr 00:1a:92:7d:69:f6  
          inet addr:169.254.9.40  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:247 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:177136 (172.9 KB)  TX bytes:177136 (172.9 KB)

```

  I have a static IP for eth0, and eth1 uses dhcp.  I was hoping one of them would come up.  I have set both to static IPs and both to dhcp, and nothing works.  I don't know what avahi is, or why I have it - I guess dhcp?

My /etc/network/interfaces:
```

auto lo
iface lo inet loopback




iface eth1 inet dhcp
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1



auto eth0
iface eth0 inet static
address 192.168.1.201
netmask 255.255.255.0
gateway 192.168.1.1






auto eth1

```

---

### Post by iaculallad on 2008-06-03
Assuming your UTP cable is connected to your eth0 interface, drop to terminal and manually issue:

```
sudo ifup eth0
```

If that doesn't work, post your /var/log/syslog after that failed connection attempt.

---

### Post by benbelly on 2008-06-03
I got the already up message, so I did an ifdown, then the ifup, and syslog spit out:
```

Jun  3 20:53:15 duel avahi-daemon[5568]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun  3 20:53:15 duel avahi-daemon[5568]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.201.
Jun  3 20:53:15 duel avahi-daemon[5568]: Withdrawing address record for 192.168.1.201 on eth0.
Jun  3 20:54:30 duel kernel: [  555.295968] eth0: no link during initialization.
Jun  3 20:54:30 duel avahi-daemon[5568]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.201.
Jun  3 20:54:30 duel kernel: [  555.298131] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  3 20:54:30 duel avahi-daemon[5568]: New relevant interface eth0.IPv4 for mDNS.
Jun  3 20:54:30 duel avahi-daemon[5568]: Registering new address record for 192.168.1.201 on eth0.IPv4.

```

---

### Post by iaculallad on 2008-06-03
Could you ping your default gateway (192.168.1.1)?

---

### Post by benbelly on 2008-06-03
I can't reach it from that machine.
```

ben@duel:/etc$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.201 icmp_seq=1 Destination Host Unreachable
From 192.168.1.201 icmp_seq=2 Destination Host Unreachable
From 192.168.1.201 icmp_seq=3 Destination Host Unreachable
From 192.168.1.201 icmp_seq=4 Destination Host Unreachable
From 192.168.1.201 icmp_seq=5 Destination Host Unreachable
From 192.168.1.201 icmp_seq=6 Destination Host Unreachable

```

But I can from this one (my laptop that I'm using to post).

---

### Post by iaculallad on 2008-06-03
Try unplugging the LAN cable from your eth0 interface and connect it to your eth1.

Bring it up:

```
sudo ifup eth1
```

and ping you're default gateway

```
ping 192.168.1.1
```

to check if you have conflicting ethernet cards.

---

### Post by benbelly on 2008-06-03
No good. :(  To be honest, I don't really remember which port was which.  Both are on the mainboard, and with both not working, it's hard to tell.  :)  Anyway, I tried both interfaces with each port plugged in.

I was poking around, trying a few things and wound up back at that lshw command, and I got this:
```

        *-bridge:0
             description: Ethernet interface
             product: MCP55 Ethernet
             vendor: nVidia Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: eth0
             version: a2
             serial: 00:1a:92:7d:52:53
             width: 32 bits
             clock: 66MHz
             capabilities: bridge bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.201 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
        *-bridge:1
             description: Ethernet interface
             product: MCP55 Ethernet
             vendor: nVidia Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth1
             version: a2
             serial: 00:1a:92:7d:69:f6
             width: 32 bits
             clock: 66MHz
             capabilities: bridge bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.200 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes

```

   Which all looks good to me.  Thought I would mention it.

---

### Post by benbelly on 2008-06-04
Here's a funny thing.  I run network tools, select eth0 or eth1, and click configure, and I get this error message:

The Interface Does Not Exist

What's that about?

---

### Post by benbelly on 2008-06-05
Just for kicks, I reinstalled network-manager, network-manager-gnome, xinetd.  No good.  Any suggestions?

---

### Post by benbelly on 2008-06-10
Well, this is rather embarrassing. My BIOS was a rev out of date. I thought I had the latest. Turns out that the new version fixed some network stuff. :oops:

So, if any of you have a ASUS P5N32-E SLI, make sure you have the latest BIOS.

---

