---
title: "no network after upgrade to jaunty"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kuritsubaji on 2009-03-13
Upgraded to 9.04 and now I have no eth0 connection to the router.

The router is working fine because I'm posting this with the laptop connected on the wireless.

I've found quite a few other mentions on other threads of network issues after upgrading to jaunty.

Bug?  

More importantly, what to do next?  Go back to 8.10?

---

### Post by Crafty Kisses on 2009-03-13
What are the results of the following commands?
```
lshw -C network
lsusb
lspci
```

---

### Post by kuritsubaji on 2009-03-13
> **Codename said:**
> What are the results of the following commands?
```
lshw -C network
lsusb
lspci
```

[COLOR="Red"]results of lshw:[/COLOR]

  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:6b:6f:0f:a7:e9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A
[COLOR="Red"]
results of lsusb:[/COLOR]

Bus 002 Device 005: ID 0930:6545 Toshiba Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 001 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[COLOR="Red"]results of lspci:[/COLOR]

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
03:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a2)
04:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a2)
04:02.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a2)
05:00.0 3D controller: nVidia Corporation GeForce 9800 GX2 (rev a2)
06:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GX2 (rev a2)
09:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
09:09.0 Serial controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)
09:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
09:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
09:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

---

### Post by dmizer on 2009-03-13
Since Jaunty is still in testing, it's bound to have problems.

Moved this thread to the Jaunty testing section and closed the poll.

---

### Post by cariboo on 2009-03-13
According to what you posted, you don't have any network cards. Could you post the full output of:

```
sudo lshw -C network
```

and just in case, the nic on my nvidia motherboard shows up as a bridge device:

```
sudo lshw -C bridge
```

Use the [noparse]```
 
```[/noparse] tags to enclose the output so that it is easier to read.

Jim

---

### Post by Nullack on 2009-03-13
More fundamentally, you dont mention if your using DHCP or statically assigned addresses.

---

### Post by kuritsubaji on 2009-03-15
> **cariboo907 said:**
> According to what you posted, you don't have any network cards.

Correct. I'm using the onboard gigabit LAN on the mobo (EVGA nForce 750i SLI) 

> **cariboo907 said:**
> Could you post the full output of:

```
sudo lshw -C network
```

did that, got back the same as posted earlier with the added line:

 ```
link=yes multicast=yes
```


> **cariboo907 said:**
> and just in case, the nic on my nvidia motherboard shows up as a bridge device:

```
sudo lshw -C bridge
```

did that, here goes:

```
*-pci                   
       description: Host bridge
       product: C55 Host Bridge
       vendor: nVidia Corporation
       physical id: 100
       bus info: pci@0000:00:00.0
       version: a2
       width: 32 bits
       clock: 66MHz
     *-pci:0
          description: PCI bridge
          product: C55 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
        *-pci
             description: PCI bridge
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             version: a2
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-pci:0
                description: PCI bridge
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a2
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm pciexpress bus_master cap_list
                configuration: driver=pcieport-driver
              *-pci
                   description: PCI bridge
                   product: PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070
                   vendor: nVidia Corporation
                   physical id: 0
                   bus info: pci@0000:03:00.0
                   version: a2
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm pciexpress bus_master cap_list
                   configuration: driver=pcieport-driver
                 *-pci:0
                      description: PCI bridge
                      product: PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070
                      vendor: nVidia Corporation
                      physical id: 0
                      bus info: pci@0000:04:00.0
                      version: a2
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pci pm pciexpress bus_master cap_list
                      configuration: driver=pcieport-driver
                      resources: iomemory:d1d10-d1d0f
                 *-pci:1
                      description: PCI bridge
                      product: PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070
                      vendor: nVidia Corporation
                      physical id: 2
                      bus info: pci@0000:04:02.0
                      version: a2
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pci pm pciexpress bus_master cap_list
                      configuration: driver=pcieport-driver
                      resources: iomemory:c1c10-c1c0f
           *-pci:1
                description: PCI bridge
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                version: a2
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm pciexpress bus_master cap_list
                configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C55 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:1f:bc:07:b5:f1
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
```

---

### Post by kuritsubaji on 2009-03-15
> **Nullack said:**
> More fundamentally, you dont mention if your using DHCP or statically assigned addresses.

Here's a fundamental breakdown of the hardware involved:

nic: on-board gigabit LAN (EVGA nForce 750i SLI MoBo)

--to-- 

SMC Barricage 2804WBRP-G router/print server

I do have the router set to use a DHCP server to dynamically assign addresses to two linux desktops, one linux laptop, one windows tablet PC and one smartphone.

---

### Post by cariboo on 2009-03-15
> description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:1f:bc:07:b5:f1
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s

According to the above, the driver, **forcedeth**, is loaded for you network card.

What happens when you run in a terminal:

```
sudo dhclient eth0
```

I would also suggest you try another cable.

Jim

---

### Post by CyberPrime on 2009-03-15
I am having this same issue, wtf is the problem? I have never had an issue this big last with a beta for this long. Please help?

---

### Post by Talon2 on 2009-03-15
> **CyberPrime said:**
> I am having this same issue, wtf is the problem? I have never had an issue this big last with a beta for this long. Please help?

Alpha 6 has taken out networking here also.  The hardware is not an issue as I dual boot (Intrepid and whatever test version).  I'm typing this message from Intrepid on the same machine that has broken networking with Alpha 6.

This system works well.  The nic is a realtek 3139x and is well supported.  The setup is very generic (auto dhcp) into a dlink router.

I'll work on shooting the problem later.  This msg is simply to confirm what others are seeing.

---

### Post by kuritsubaji on 2009-03-15
> **cariboo907 said:**
> According to the above, the driver, **forcedeth**, is loaded for you network card.

What happens when you run in a terminal:

```
sudo dhclient eth0
```

results:

```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1f:bc:07:b5:f1
Sending on   LPF/eth0/00:1f:bc:07:b5:f1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.2.101 from 192.168.2.1
DHCPREQUEST of 192.168.2.101 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.101 from 192.168.2.1
bound to 192.168.2.101 -- renewal in 910320807 seconds.
```


> **cariboo907 said:**
> I would also suggest you try another cable.

Jim

Not likely since the connection is fine if I boot to the 8.04 partition or if I swap out the hard drive for the one with the KDE installation.

BTW: I thought I should mention that I'm running the 2.6.27-11 kernel because the 2.6.28-9 kernel won't run for some reason.  Just freezes at "Starting up..." with a blinking cursor and no hard drive activity; for an inordinate amount of time.

---

### Post by yooboontoo on 2009-03-16
I have a less serious problem with networking.

Networking works but...

The "NetworkManager" applet in Gnome shows that there is no network connection and Firefox always starts up with "Work Offline" checked.

If I try to "connect" using the applet it actually disconnects the network.

---

### Post by fonsi2099 on 2009-03-17
The same probleme to me, after upgrading and new installation of jaunty, with windows vista it does work well
Thanks 
Fonsi  :popcorn: :(

---

### Post by jjpcexpert on 2009-03-17
> **CyberPrime said:**
> I am having this same issue, what is the problem? I have never had an issue this big last with a beta for this long. Please help?

What I changed to What in my quote of you was a bad word.

---

### Post by scaine on 2009-03-17
> **kuritsubaji said:**
> results:

```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1f:bc:07:b5:f1
Sending on   LPF/eth0/00:1f:bc:07:b5:f1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.2.101 from 192.168.2.1
DHCPREQUEST of 192.168.2.101 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.101 from 192.168.2.1
bound to 192.168.2.101 -- renewal in 910320807 seconds.
```

Well, that sure looks like your router, 192.168.2.1 just gave eth0 the IP address of 192.168.2.101.

What exactly is the issue here?  Can you try some pings, please, below?

```
ping 192.168.2.1
ping 80.75.64.122
ping www.cnet.com
```That might help narrow down what's happening.  Also, please do this :

```
sudo apt-get install ethtool
sudo ethtool eth0
```and post back the results.

[EDIT : I'm an idiot - you probably can't apt-get anything, since you don't have network.  And ethtool only really gives the same info as above, only much more readable... I'm gutted that it's not part of the standard Jaunty install, cos I could have sworn it was in previous Ubuntu versions]

Probably also useful to see your DNS entries :
```

cat /etc/resolv.conf  (note, NOT resolve.conf - sorry about that)

```Thanks.

---

### Post by fonsi2099 on 2009-03-20
cat /etc/resolve.conf
there is no output from this line,  
I put this line in a terminal, with or without sudo privileges;  what I'm doing wrong!

---

### Post by taavikko on 2009-03-20
> **fonsi2099 said:**
> cat /etc/resolve.conf
there is no output from this line,  
I put this line in a terminal, with or without sudo privileges;  what I'm doing wrong!

The name of the file, it's 
/etc/resolv.conf

```
cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.254

```

---

### Post by bgiannes on 2009-03-20
i have the same problem....


i unpluged another PC connected to the LAN, which the 9.04 box was connected to va smb mount, 9.04 went into a kernel panic and on reboot the network was gone....

---

### Post by bgiannes on 2009-03-20
is this a solution?


[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/315370](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/315370)

bug in ipmasq? i'm running ubuntu server, so is it a standard package?

$ sudo etc/init.d/ipmasq stop

network works again?

if it is the problem i would do a..
sudo apt-get remove ipmasq


ps, i never had network-manager install, so that's not the problem, (well for me anyway) 

i will try it tonight....

---

### Post by zika on 2009-03-21
in 8.10 I had NM disabled. it, simply, did not work on my machines. I kept in only for wireless on portables. since I did clean install on my main machine it came again with 9.04. I had to try it. it stayed ON and I love it. now it is as it was supposed to be. everything I could do through /etc/network/interfaces and /etc.resolv.conf I can do now through NM ... I would have never thought I would write something like this a month ago, not to say in October 2008. :) even on machines that were upgraded I keep turning NM ON. great resurrection ... !

---

### Post by CyberPrime on 2009-03-21
Still having trouble here, fellas. The ipmasq thing didn't work, said I didn't have ipmasq installed. I am going to try and get firestarter installed and see if I can repair the IPTables. Is nobody paying attention to this?

EDIT: I flushed the iptables, didn't help.

---

### Post by scaine on 2009-03-21
Yeah, I'm still paying attention, but the OP hasn't posted for a while (and didn't do any of the tests I asked for), so we're in the dark a bit here.

As for firestarter, it's maybe worth a shot, but I'd use GUFW personally, since uncomplicated firewall is already on your build.  I just don't know how you're going to get anything installed (easily) if you've no network connection...

I suppose you don't need GUFW - try using the command line for UFW :
```
sudo ufw disable

```
Worth a shot?

---

### Post by CyberPrime on 2009-03-23
Sadly, disabling the firewall didn't work. :( Any other ideas?

---

### Post by scaine on 2009-03-23
Show me the output of those pings I mentioned earlier please.  That will help diagnose the fault :

1. Ping your default gateway (e.g if you have, say, 192.168.1.10, then ping 192.168.1.1)

2. Ping something on the internet that usually responds, like the opendns servers : 208.67.222.222

3. Ping a named host, like [www.cnet.com](www.cnet.com)

---

### Post by estamand on 2009-03-25
The resolution i have (temporarily i guess) was to modify the /etc/network/interfaces file to read:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

I removed the references to br0 for now.  This is what I needed to get my jaunty alpha 6 online.

---

### Post by JarekMk on 2009-04-12
Hello,

I have this same problem. DFI motherboard, nForce 4 chip.
On Ubuntu 8.04 network works fine - on 8.10 don't see network - I'm useing DHCP on Asmax router / static IP from ISP.

What is wrong? No nvidia modules in kernel? How can I check it? I want to migrate to Ubuntu x64 9.04, but can't without network connections... (

Thanks for any help.

Regards and Merry Christmas :)

---

