---
title: "[SOLVED] xubuntu for ppc powerbook G3 -- internet not working"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by stretch44 on 2008-03-04
Hi there,

I found my girlfriend's old powerbook g3 ("lombard") in her closet, and thought I might put Xubuntu on it.  It's a small system, and OS X was running slowly when accessing the internet.

I just finished installing 7.0.4, but the internet doesn't work now.  Tinkering with the settings in the Network application doesn't seem to help.

My home network is simple and is working with my other laptop fine.  The powerbook has a built-in ethernet adapter and an aftermarket belkin wireless network card.  Before I go about messing with wireless though, I'd like to get wired working.

Here's some of the output from my testing around.
```

> sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:E4:C5:8E:65  
          inet6 addr: fe80::250:e4ff:fec5:8e65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5820 (5.6 KiB)
          Interrupt:42 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:50:E4:C5:8E:65  
          inet addr:169.254.8.153  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1232 (1.2 KiB)  TX bytes:1232 (1.2 KiB)

> sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 4676
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:e4:c5:8e:65
Sending on   LPF/eth0/00:50:e4:c5:8e:65
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

> route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0

```

Any suggestions?

Many thanks,
--Ed

---

### Post by Gen2ly on 2008-03-04
Perhaps this thread can help:

[http://ubuntuforums.org/showthread.php?p=4438232](http://ubuntuforums.org/showthread.php?p=4438232)

looks like the gateway is missing.  route can add it.

---

### Post by stretch44 on 2008-03-04
Thanks for the suggestion!  

I played around with adding the gateway with route, but no progress.  I'm still not able to ping the router.

Here's what I tried, precisely:

```

ed@lombard:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:E4:C5:8E:65  
          inet6 addr: fe80::250:e4ff:fec5:8e65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5171 (5.0 KiB)
          Interrupt:42 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:50:E4:C5:8E:65  
          inet addr:169.254.8.153  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4176 (4.0 KiB)  TX bytes:4176 (4.0 KiB)

ed@lombard:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
ed@lombard:~$ sudo ifconfig eth0 down
ed@lombard:~$ sudo route add default gw 192.168.1.1
ed@lombard:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
ed@lombard:~$ sudo ifconfig eth0 up
ed@lombard:~$ ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 127.0.0.1 icmp_seq=1 Destination Host Unreachable
From 127.0.0.1 icmp_seq=2 Destination Host Unreachable
From 127.0.0.1 icmp_seq=3 Destination Host Unreachable
From 127.0.0.1 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3009ms
, pipe 3
ed@lombard:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:E4:C5:8E:65  
          inet6 addr: fe80::250:e4ff:fec5:8e65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:1 overruns:0 frame:1
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:9427 (9.2 KiB)
          Interrupt:42 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:50:E4:C5:8E:65  
          inet addr:169.254.8.153  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5800 (5.6 KiB)  TX bytes:5800 (5.6 KiB)


```

---

### Post by dstew on 2008-03-04
Can you post the values that your network router is set up with? IP address, gateway, netmask, whether DHCP server is activated or not. Are you sure the cable is plugged into a working socket? Is the cable OK? It seems that the ethernet card is not hearing any traffic.

---

### Post by stretch44 on 2008-03-04
For the LAN: 
Router IP is 192.168.1.1  (also used as the Gateway for systems connected behind the router.)  
Subnet Mask is 255.255.255.0
DHCP server is Enabled and is used by my other system which snagged 192.168.1.100
After not getting DHCP to work, I tried using Static IP on the Xubuntu PowerBook, (asking for 192.168.1.110) and didn't get anywhere.

The cable and the router are both working fine.  Supposing that the ethernet socket is malfunctioning on the PowerBook, I'd have to get the Belkin wireless adapter up and running.  This means getting the Windows drivers from Belkin (done), and loading ndiswrapper onto the Xubuntu system, (right?).  

Since I can't use apt-get 'til I get on the net, where would I find a .tgz or .rpm for ndiswrapper that's compatible with 7.0.4.  How much trouble will I see with dependencies in installing this?

---

### Post by dstew on 2008-03-04
The best site for off-line program installation is [nonetdebs]("http://nonetdebs.homeip.net/"). You get an account with them (free) then you get custom downloads for the packages with all the dependencies. Check it out.

---

### Post by stretch44 on 2008-03-05
I tried out nonetdebs, (which is a pretty cool site, btw).  But no dice.  I'm not sure if it's not compatible with Xubuntu, or what.  I downloaded the following debs:
```
dpkg -i ./dpkg-dev_1.13.24ubuntu6_all.deb
dpkg -i ./html2text_1.3.2a-3_powerpc.deb
dpkg -i ./gettext_0.16.1-1ubuntu2_powerpc.deb
dpkg -i ./intltool-debian_0.35.0+20060710.1_all.deb
dpkg -i ./po-debconf_1.0.8_all.deb
dpkg -i ./debhelper_5.0.42ubuntu1_all.deb
dpkg -i ./module-assistant_0.10.10_all.deb
dpkg -i ./ndiswrapper-source_1.38-1ubuntu1_all.deb
# Resolve dependencies left unset or broken packages.
apt-get install -f
#EOF
```
The output:
```
Selecting previously deselected package dpkg-dev.
(Reading database ... 79483 files and directories currently installed.)
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Selecting previously deselected package html2text.
(Reading database ... 79559 files and directories currently installed.)
Unpacking html2text (from .../html2text_1.3.2a-3_powerpc.deb) ...
Setting up html2text (1.3.2a-3) ...

Selecting previously deselected package gettext.
(Reading database ... 79571 files and directories currently installed.)
Unpacking gettext (from .../gettext_0.16.1-1ubuntu2_powerpc.deb) ...
Setting up gettext (0.16.1-1ubuntu2) ...

Selecting previously deselected package intltool-debian.
(Reading database ... 79768 files and directories currently installed.)
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Setting up intltool-debian (0.35.0+20060710.1) ...
Selecting previously deselected package po-debconf.
(Reading database ... 79777 files and directories currently installed.)
Unpacking po-debconf (from ./po-debconf_1.0.8_all.deb) ...
Setting up po-debconf (1.0.8) ...
Selecting previously deselected package debhelper.
(Reading database ... 79808 files and directories currently installed.)
Unpacking debhelper (from .../debhelper_5.0.42ubuntu1_all.deb) ...
Setting up debhelper (5.0.42ubuntu1) ...
Selecting previously deselected package module-assistant.
(Reading database ... 80063 files and directories currently installed.)
Unpacking module-assistant (from .../module-assistant_0.10.10_all.deb) ...
Setting up module-assistant (0.10.10) ...
Selecting previously deselected package ndiswrapper-source.
(Reading database ... 80112 files and directories currently installed.)
Unpacking ndiswrapper-source (from .../ndiswrapper-source_1.38-1ubuntu1_all.deb) ...
Setting up ndiswrapper-source (1.38-1ubuntu1) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
But testing it out:
```
$ which ndiswrapper
/usr/bin/ndiswrapper
$ ndiswrapper
Error: no version of ndiswrapper found!
$ ndiswrapper --help
Error: no version of ndiswrapper found!

```

So, to recap:  

I don't know why the ethernet connection isn't working.  

Gave up on that, moved to getting wireless adapter working.  

Having trouble getting a version of ndiswrapper to load without the net, though.

---

### Post by dstew on 2008-03-05
Looks like you installed ndiswrapper-source. This is the source-file package, used to compile from source code. The packages you need are (I think) **nsdiwrapper-common** and **ndiswrapper-utils**. These are binary (working program) files.

---

### Post by stretch44 on 2008-03-05
Oops.

Unfortunately, in the 4 repositories I checked (Main, Universe, Restriced, and Multiverse), I couldn't find any Feisty PowerPC deb pkgs for ndiswrapper-utils.  Would downloading the ndiswrapper-utils for "Edgy" work?  The repository lists it as compatible with all architectures.

Also, I did try ndiswrapper-common on its own.  Here's the output:
```
ed@lombard:~/Downloads/dpkg/ndiswrapper$ sudo bash load_ndiswrapper_script 
(Reading database ... 80121 files and directories currently installed.)
Preparing to replace ndiswrapper-common 1.38-1ubuntu1 (using .../ndiswrapper-common_1.38-1ubuntu1_all.deb) ...
Unpacking replacement ndiswrapper-common ...
Setting up ndiswrapper-common (1.38-1ubuntu1) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ed@lombard:~/Downloads/dpkg/ndiswrapper$ sudo ndiswrapper
Error: no versions of ndiswrapper found!

```

---

### Post by dstew on 2008-03-05
Ah, I am afraid I have led you astray. Ndiswrapper will not work at all on a PowerPC, since the program needs to run the x86 code from the Windows driver. Sorry. See the [PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ").

You might be able to get it going using the Windows emulator Qemu. [Here]("http://lists.terrasoftsolutions.com/pipermail/yellowdog-general/2004-December/017120.html") is a forum post where someone claims that someone said they could use ndiswrapper with Qemu.

EDIT: I notice that you have the eth0:avah interface, that did seem to get an IP address. Maybe if you disable this interface your eth0 will work instead. [Here]("http://ubuntuforums.org/showthread.php?t=693562") is a thread where this interface was disabled.
EDIT again: Maybe you just have to set up your internet connection on eth0:avah instead of eth0. Look in the Networking menu item (if Xubuntu has one, can't remember).

---

### Post by stretch44 on 2008-03-05
Success!  I'm online!

dstew, I looked over the Ubuntu FAQ for PPC that you sent me.  It pointed out that 6.10 was the last supported version of Ubuntu for the architecture.  So, I tried formatting again and loading Xubuntu 6.10.  Between the networking setup and running dhclient, I have a connection via ra0 (the Belkin wireless adapter).  No ndiswrapper needed!

Many thanks for all your help.

---

