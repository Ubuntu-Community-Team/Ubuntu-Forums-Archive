---
title: "Just installed 7.10 - can't connect to internet at all"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by soulgt on 2008-01-20
Hi there. Like the title says, I've been trying to install 7.10 on my dell latitude d600 for a while now with little success. The OS installs, looks gorgeous... but refuses to connect to the internet (wired). The connection works, because I'm posting this right now with it. (EDIT: I'm posting with the ethernet cable plugged into windows desktop machine - just making the point that it's not a faulty internet connection. I would simply like to make it work with the laptop that's now running Ubuntu)

I am new to Ubuntu and Linux, but definitely interested in learning. Getting this machine up and running would certainly help. I've looked around this forum, and have tried things like:
[LIST]
[*]disabling ipv6 in Firefox about:config
[*]reinstalling while wired up (no luck)
[*]trying every possible permutation of the network settings I could think of
[/LIST]

Below are the results for me for the commands everyone seems to ask for in these types of posts:
lspci -nn
sudo lshw -C network
ifconfig

Any advice or guidance would be greatly appreciated - I just feel so frustrated and stuck right now.

```
arun@satchmorun:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 01)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet [14e4:16a6] (rev 02)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 02)


arun@satchmorun:~$ sudo lshw -C network
[sudo] password for arun:
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:d6:e2:39
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5702-v2.25 latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:2d:52:39
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=32 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g


arun@satchmorun:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:D6:E2:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20200 (19.7 KB)  TX bytes:20200 (19.7 KB)
```

---

### Post by soulgt on 2008-01-20
Sorry for the bump - I waited until I got moved down to page 3 without any replies, figured that's the point of oblivion. 

I do acknowledge that I'm new to this and am probably just overlooking something simple - I would certainly still appreciate a response to get me headed in the right direction.

Thanks!

---

### Post by soulgt on 2008-01-21
One more bump. I've been scouring the forums trying all manners of different solution. It remains the case that I can't connect to the internet. 

When running ethtool eth0, it tells me that it detects a link, which I'm assuming is a good thing. 

I'm on the verge of giving up - thought I'd throw one last bump in here, see if I could perhaps get a response.

---

### Post by haaglin on 2008-01-21
> but refuses to connect to the internet (wired). The connection works, because I'm posting this right now with it.

You say you can't connect to internet, but you are posting from the computer now? This doesn't make any sense.

---

### Post by soulgt on 2008-01-21
> **haaglin said:**
> You say you can't connect to internet, but you are posting from the computer now? This doesn't make any sense.

Perhaps I wasn't being clear. I have a cable modem, and 2 computers. One is my main desktop, running boring old Windows Vista, from which I am making these posts. The other is my old Dell Latitude d600 laptop, which I've decided to convert to a linux learning machine. 

When I plug the ethernet cable into this machine, it works, which is the point I was trying to make.

When I plug it into my new Ubuntu installation, the connection does not work, and this is what I'm requesting some assistance with.

---

### Post by c0met on 2008-01-21
The below thread would be really worth your while to look at. It is really comprehensive.

[http://ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf]("http://ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf")

---

### Post by haaglin on 2008-01-21
is your router configured with dhcp? what happens if you write: 
```

sudo dhclient eth0

```

If you plug it directly into the modem, check your settings in Vista. You may need to set an static ip and configure dns.

---

### Post by soulgt on 2008-01-21
> **haaglin said:**
> is your router configured with dhcp? what happens if you write: 
```

sudo dhclient eth0

```

If you plug it directly into the modem, check your settings in Vista. You may need to set an static ip and configure dns.

sudo dhclient eth0 output:
```
arun@satchmorun:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 6778
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0b:db:d6:e2:39
Sending on   LPF/eth0/00:0b:db:d6:e2:39
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
arun@satchmorun:~$ 

```

Vista ipconfig /all output:
```

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Octavio
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : socal.rr.com

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : socal.rr.com
   Description . . . . . . . . . . . : Marvell Yukon 88E8039 PCI-E Fast Ethernet Controller
   Physical Address. . . . . . . . . : 00-1B-B9-8C-A0-83
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::c41:988d:ec41:f2fb%8(Preferred)
   IPv4 Address. . . . . . . . . . . : 76.167.225.75(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Lease Obtained. . . . . . . . . . : Sunday, January 20, 2008 11:45:57 PM
   Lease Expires . . . . . . . . . . : Tuesday, January 22, 2008 12:59:05 AM
   Default Gateway . . . . . . . . . : 76.167.224.1
   DHCP Server . . . . . . . . . . . : 10.226.128.1
   DHCPv6 IAID . . . . . . . . . . . : 201333689
   DNS Servers . . . . . . . . . . . : 66.75.164.90
                                       66.75.164.89
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 6:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e50:10a4:1d93:b358:1eb4(Preferred)
   Link-local IPv6 Address . . . . . : fe80::10a4:1d93:b358:1eb4%9(Preferred)
   Default Gateway . . . . . . . . . :
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 7:

   Connection-specific DNS Suffix  . : socal.rr.com
   Description . . . . . . . . . . . : isatap.socal.rr.com
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::200:5efe:76.167.225.75%10(Preferred)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 66.75.164.90
                                       66.75.164.89
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 9:

   Connection-specific DNS Suffix  . : socal.rr.com
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Temporary IPv6 Address. . . . . . : 2002:4ca7:e14b::4ca7:e14b(Preferred)
   Default Gateway . . . . . . . . . : 2002:c058:6301::c058:6301
   DNS Servers . . . . . . . . . . . : 66.75.164.90
                                       66.75.164.89
   NetBIOS over Tcpip. . . . . . . . : Disabled
```

Not that I actually *know*, but it would seem that having DHCP enabled and working in Vista would mean that setting a static IP isn't necessary in Ubuntu. Add to that the fact that one of the many things I tried was setting a static IP using the Network Manager, which still didn't work.

And I have set the DNS addresses in the DNS tab of network manager to the DNS servers shown above.

---

### Post by haaglin on 2008-01-21
Ok. it seems like you dont recieve any ip adress from the modem. Have you added the default gateway? post the output from:
```
route
```

---

### Post by soulgt on 2008-01-21
> **haaglin said:**
> Ok. it seems like you dont recieve any ip adress from the modem. Have you added the default gateway? post the output from:
```
route
```

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
```

---

### Post by haaglin on 2008-01-21
try this:

```

sudo route add default gw 76.167.224.1
sudo dhclient eth0

```

---

### Post by c0met on 2008-01-21
I often have to "kick start" my modem because it doesn't always give me an IP address. What I do is to right click on the network icon and un-check "enable networking". Then I right click and re-enable it. That's all my modem need to get working.

As mentioned before, the link above that I posted earlier is VERY comprehensive and might have a solution for you.

---

### Post by Zack McCool on 2008-01-21
> **soulgt said:**
> Perhaps I wasn't being clear. I have a cable modem, and 2 computers. One is my main desktop, running boring old Windows Vista, from which I am making these posts. The other is my old Dell Latitude d600 laptop, which I've decided to convert to a linux learning machine. 

When I plug the ethernet cable into this machine, it works, which is the point I was trying to make.

When I plug it into my new Ubuntu installation, the connection does not work, and this is what I'm requesting some assistance with.

Do you have a router between the PCs and the Cable Modem, or are you connecting directly to the cable modem?

If you are connecting directly to the cable modem, you'll have to turn it off (or unplug it) when you make the switch.  The cable modem is still using the MAC from your desktop, and everything gets a bit confused...

---

### Post by Glugglug on 2008-01-21
I had the same problem  when installing  7.10 tried unplugging the power supply from the router but that didn't work  so reinstalled 7.04  .

---

### Post by soulgt on 2008-01-21
> **haaglin said:**
> try this:

```

sudo route add default gw 76.167.224.1
sudo dhclient eth0

```

I did that, then checked with route to make sure it worked, still received no dhcpoffers:
```
arun@satchmorun:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         76.167.224.1    0.0.0.0         UG    0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
arun@satchmorun:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 8100
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0b:db:d6:e2:39
Sending on   LPF/eth0/00:0b:db:d6:e2:39
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
arun@satchmorun:~$ 

```

I suppose I need to also add the mask? How exactly do I do that?

@c0met: I read through the link, and it seemed it was about 2 things: disabling ipv6 and setting up dns. I followed the instructions for the dns, using the dns server information from my Vista settings - no dice.

---

### Post by soulgt on 2008-01-21
> **Zack McCool said:**
> Do you have a router between the PCs and the Cable Modem, or are you connecting directly to the cable modem?

If you are connecting directly to the cable modem, you'll have to turn it off (or unplug it) when you make the switch.  The cable modem is still using the MAC from your desktop, and everything gets a bit confused...

Holy crap, that took care of it. Like magic. I can't believe it was that simple.

So the cable modem can only handle one MAC at a time?

Thank you all for your help, it's much appreciated. Hopefully I'll learn enough eventually to be able to help others out - for now, it's astonishing to me how much some of you know.

---

### Post by c0met on 2008-01-21
Hi soulgt,

If you get a chance, it's probably a good idea to edit your original post in the thread so that the topic has [SOLVED] in front of it. That way if people search and come across these posts, they'll know it's a good idea to read them.

Glad to read that you fixed it :)

---

