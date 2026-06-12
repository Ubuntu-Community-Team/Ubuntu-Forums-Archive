---
title: "Kaid | Firehol | Moblock = need help with connectivity"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by shookone on 2006-10-19
[COLOR="Red"]xlink issue SOLVED

My problems with kaid was not really related to firehol and moblock what so ever.

I was thinking about my ip setup and realized the port i chose to use was on the cable modems network. So that subnet was messing me up. I switched to a different subnet and now xbox sees all games on xlink.

i have a Webstar cable modem that uses the subnet 192.168.100.0 (ISP SETUP?) and my network was in the 100's for some reason. Bad luck?.

So i went to traditional 192.168.1.0 network and im all up and running.

I can browse without timing out and can play games.[/COLOR]



[I]Hello..

I'm having a little trouble getting kaid to work with firehol. I can send data.. but cannot receive.. i don't see pings i dont see new rooms... When the firewall is off it works.

kaid is tool that emulates a LAN for online gaming (system link in xbox)

[www.teamxlink.co.uk](www.teamxlink.co.uk)

firehol.conf:
```

version 5

#specify ports here
## type: client or server
## label: label port
## type/port: tcp or udp and port (Ex. tcp/80 or udp/300000
#format: type_label_ports="type/port"

server_xlink_ports="udp/37500"
server_xlinkx_ports="udp/34522"
server_1024_ports="udp/1024"
client_xlink_ports="default"

dnat to 192.168.100.2:37500 inface eth0 proto udp dport 37500

# moblock settings
iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE

# The network of eth1
home_ips=192.168.100.2/24


# Your internet interface

interface eth0 internet src not "${home_ips} ${UNROUTABLE_IPS}"

        protection strong 10/sec 10
        server "ssh ftp" accept # you dont need xlink here
        # This will send http traffic directly to accept instead of moblock thus whitelisting it...
        client "http https" accept
        client all MOBLOCK

# Local network

interface eth1 home src "${home_ips}" #this is only in your lan...
        policy accept
        client all accept
        server all accept # you can safely remove this comment

#Routing information

router home2internet inface eth0 outface eth1
        masquerade reverse
        client all accept
        server xlink accept # xlink only here (this is the server)

```

ethereal shows that packets are sent but not returned. Traffic on port 34522 is what I assume is the port that is not working.

```
No.     Time        Source                Destination           Protocol Info
      3 2.224676    192.168.100.10        192.168.100.2         UDP      Source port: 1024  Destination port: 34522

Frame 3 (109 bytes on wire, 109 bytes captured)
Ethernet II, Src: Microsof_5f:80:b1 (00:0d:3a:5f:80:b1), Dst: Lite-OnC_d9:56:60 (00:a0:cc:d9:56:60)
Internet Protocol, Src: 192.168.100.10 (192.168.100.10), Dst: 192.168.100.2 (192.168.100.2)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
    Total Length: 95
    Identification: 0x0d4b (3403)
    Flags: 0x00
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0x23e6 [correct]
    Source: 192.168.100.10 (192.168.100.10)
    Destination: 192.168.100.2 (192.168.100.2)
**User Datagram Protocol, Src Port: 1024 (1024), Dst Port: 34522 (34522)**
Data (67 bytes)

0000  4b 41 49 5f 43 4c 49 45 4e 54 5f 56 45 43 54 4f   KAI_CLIENT_VECTO
0010  52 3b 41 72 65 6e 61 2f 58 42 6f 78 2f 46 69 72   R;Arena/XBox/Fir
0020  73 74 20 50 65 72 73 6f 6e 20 53 68 6f 6f 74 65   st Person Shoote
0030  72 2f 48 61 6c 6f 20 32 2f 41 6d 65 72 69 63 61   r/Halo 2/America
0040  73 3b 3b                                          s;;


```

cat /etc/kaid.conf:

```
################################################################################
# Kai Engine Configuration File
#
# This file contains the configuration options for Kai Engine.
# There are some fields which can be modified, the descriptions of these fields
# and their default values are listed below
#

# Verbosity             : Debug output verbosity. Options are as follows:
#                         0 - Silent apart from starting / stopping messages, and init failures.
#                         1 - As 1, but shows import events such as UI attach/detach, console detection,
#                             orb connection / loss.
#                         2 - As 2, but more detailed, showing thread start/stop events, DHCP
#                             events, and other important information.
#                         3 - Debug - same as 2, but with lots of extra information - useful
#                             for diagnosing segfaults etc.
Verbosity = 2

# User                  : Specifies which system user to switch to after having
#                         allocated necessary privileged resources. (FreeBSD Only!)
User = daemon

# UIBind                : Specifies which ip/port kaid will use to listen for controller
#                         UIs. You don't want to change this.
UIBind = :34522

# OrbPort               : Specifies which port kaid will use to probe(UDP) and talk to
#                         Orbitals (TCP) . You don't want to change this.
OrbPort = 34525

# OrbDeepPort           : Specified which port kaid will use to probe and talk to
#                         deep resolution servers.  You don't want to change this.
OrbDeepPort = 34523

# EngineBind            : Specifies the IP:port to listen for the engine (UDP socket);
#                         (port should be forwarded in your router if using NAT)
#                         Ex.: 69.69.69.69, 69.69.69.69:37500, :37500
EngineBind = :37500

# EngineDeepBind        : Specifies the IP:port to listen for the engine (deep resolution)
#                         Do not enable this unless directed to.
#                         EngineDeepBind must be a different port than EngineBind if
#                         they use the same IP address
#                         Ex.: 69.69.69.69, 69.69.69.69:37501, :37501
EngineDeepBind = :0

# Engine PAT            : Tells the orbital server to use your perceived UDP port, as opposed to the
#                         one specified in EngineBind. Ignored if EngineBind is 0. Please don't turn this
#                         setting to 1, unless directed to do so in a troubleshooting session.
EnginePAT = 0

# SniffDevice           : NIC to sniff for console traffic (eth0, ethX, ...). Will be used
#                         for packet injection too.
#                         Ex.: eth0 (default), en0 (Mac OSX), br0 (WRT54G)
SniffDevice = eth1

# LocalDevices          : How many consoles to detect before the engine locks the pcap filter. Setting this to 0,
#                         means the engine will never lock - which means you can use any number of consoles, but
#                         you will notice a performance hit, if your network is busy with other traffic. The best
#                         thing to do here is to set the number to the number of consoles you own - that's why it
#                         defaults to 1 - because most people have just 1 console.
LocalDevices = 1

# ConfigURL             : URL where orb list is published (and extra stuff) - best not to mess with this.
ConfigURL = www.teamxlink.co.uk/connector/clientgetconfig.php

# ConfigCache           : Location of cached orb list - this file is used if the ConfigURL is inaccessible
#                         Make sure this file is writable.  WRT54G users might want to change it to a non-volatile
#                         location if that feature is available in their firmware
#                         (i.e. /jffs/tmp/ for DD-WRT, /usr/local/ for Sveasoft)
ConfigCache = /tmp/kaiSystemConfig.txt

# CacheFile             : Location of Kai engine cache information
#                         Make sure this file is writable.  WRT54G users might want to change it to a non-volatile
#                         location if that feature is available in their firmware
#                         (i.e. /jffs/tmp/ for DD-WRT, /usr/local/ for Sveasoft)
CacheFile = /tmp/kaiEnginePersist.txt

#Authentication         : Set username and password and AutoLogin=1 for an easy life...
Username = username
Password = password
AutoLogin = 1

# Xbox DHCP setting     : Please leave alone, unless playing with emulators or DoomX etc. You DO NOT need this set to 1
#                         to use XBMC as a dashboard - setting it to 1 will *break* your dashboards internet connectivity.
XBoxHomebrew = 0
```


Can someone help me resolve this issue. I know its a problem between my xbox (192.168.100.10) communicating with eth1 (192.168.100.2)

Ill post anything you need.[/I]

---

### Post by shookone on 2006-10-22
This is some traffic logs taken from ethereal. Seems like the problem packet is the one i labeled in red. 

Question: What is wrong with my firehol.conf 

I'll keep those who view this thread updated. Hopefully someone will respond soon.

I'm currently reading through documentation for firehol and reading manuals.

```

No.	 "Time"		 "Source"	 	 "Destination"	 	"Protocol"	 "Info"	
56	 "24.245187"	 "Microsof_5f:80:b1"	 "Lite-OnC_d9:56:60"	 "ARP"	 	"192.168.100.10 is at 00:0d:3a:5f:80:b1"	
1240	 "44.270899"	 "192.168.100.10"	 "192.168.100.2"	 "UDP"	 	"Source port: 1026  Destination port: 34522"	
[COLOR="Red"]**1399	 "44.402262"	 "192.168.100.2"	 "192.168.100.10"	 "UDP"	 	"Source port: 34522  Destination port: 1026"	 Problem packet.**[/COLOR] 
13	 "6.716853"	 "192.168.100.10"	 "255.255.255.255"	 "UDP"	 	"Source port: 4905  Destination port: 4905"	
55	 "24.245097"	 "Lite-OnC_d9:56:60"	 "Microsof_5f:80:b1"	 "ARP"	 	"Who has 192.168.100.10?  Tell 192.168.100.2"
```

---

### Post by shookone on 2006-10-22
By the way

My firehol and moblock configurations are working fine. Moblock is blocking everything it needs to. 

[INDENT][http://moblock.berlios.de/](http://moblock.berlios.de/)

MoBlock is a linux console application that blocks connections from/to hosts listed in a file in peerguardian format (guarding.p2p). It uses iptables ipqueue userspace library and it is very light in resource usage (cpu, ram).[/INDENT]

kaid is working properly. When my firewall (fireHOL) is down I am able to connect and play. Thus basically it being a fireHOL problem. 

I have found the problem ports not being routed by my firewall. Just gotta figure out the right way of wording the conf file.

In any event I am sure there are people going to have this problem im having somewhere out there. So i will post my solution to this.

---

### Post by shookone on 2006-10-22
Turns out MoBlock was blocking a kai orbital server. 

MoBlock log file:
```
Blocked OUT: ServerBeach,hits: 1,DST: 66.135.32.175
Blocked OUT: ServerBeach Emule servers|P2P Fakes,hits: 1,DST: 64.34.165.84
Blocked IN: ServerBeach Emule servers|P2P Fakes,hits: 2,SRC: 64.34.165.84
Blocked IN: ServerBeach,hits: 2,SRC: 66.135.32.175
```

so in firehol.conf file i inserted these lines shortly after the moblock settings:

```
iptables -I OUTPUT -d 66.135.32.175 -j ACCEPT
iptables -I OUTPUT -d 64.34.165.84 -j ACCEPT
iptables -I INPUT -s 66.135.32.175 -j ACCEPT
iptables -I INPUT -s 64.34.165.84 -j ACCEPT

```

here is my current firehol.conf:

```
version 5

#specify ports here
## type: client or server
## label: label port
## type/port: tcp or udp and port (Ex. tcp/80 or udp/300000
#format: type_label_ports="type/port"

server_xlink_ports="udp/37500"
client_xlink_ports="default"

dnat to 192.168.100.2:37500 inface eth0 proto udp dport 37500

# moblock settings
iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE

# IP White Listing
# (Examples)
# iptables -I OUTPUT -d a.b.c.d -j ACCEPT   | Single IP
# iptables -I OUTPUT -d a.b.c.0/24 -j ACCEPT| Net with Netmask
# iptables -I INPUT -s a.b.c.d -j ACCEPT
# iptables -I INPUT -s a.c.c.0/24 -j ACCEPT

#kai orbital servers
iptables -I OUTPUT -d 66.135.32.175 -j ACCEPT
iptables -I OUTPUT -d 64.34.165.84 -j ACCEPT
iptables -I INPUT -s 66.135.32.175 -j ACCEPT
iptables -I INPUT -s 64.34.165.84 -j ACCEPT

# The network of eth1
home_ips=192.168.100.2/24


# Your internet interface

interface eth0 internet src not "${home_ips} ${UNROUTABLE_IPS}"

        protection strong 10/sec 10
        server "ssh ftp" accept # you dont need xlink here
        # This will send http traffic directly to accept instead of moblock thus whitelisting it...
        client "http https" accept
        client all MOBLOCK

# Local network

interface eth1 home src "${home_ips}" #this is only in your lan...
        policy accept
        client all accept
        server all accept # you can safely remove this comment

#Routing information

router home2internet inface eth0 outface eth1
        masquerade reverse
        client all accept
        server xlink accept # xlink only here (this is the server)

```

---

### Post by shookone on 2006-10-22
Turns out that didn't help much in my problem. I am able to see games and go into games. But im not getting data returned as to pings, chats, refreshes.

Data is going to its target but responces are not making it back. Please help. I'm still investigating on my own of course. 

When i get a definitive solution i'll post. Sorry for the false alarm.

---

### Post by shookone on 2006-10-27
Turns out that even when i run a client locally on the linux box it still experiences the same as if it where the xbox connecting to the UI.

I'll post progress.

---

### Post by shookone on 2006-10-30
[COLOR="Red"]xlink issue SOLVED[/COLOR]

My problems with kaid was not really related to firehol and moblock what so ever.

I was thinking about my ip setup and realized the port i chose to use was on the cable modems network. So that subnet was messing me up. I switched to a different subnet and now xbox sees all games on xlink.

i have a Webstar cable modem that uses the subnet 192.168.100.0 (ISP SETUP?) and my network was in the 100's for some reason. Bad luck?.

So i went to traditional 192.168.1.0 network and im all up and running.

I can browse without timing out and can play games.

---

