---
title: "Network problems with Dell 521 on AMD Dapper Drake"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by kwilliams0 on 2006-12-08
Hello,

I have successfully installed Dapper Drake on my new Dell 521 Dimension Desktop.  However my networking doesn't work.  Specifically, I have an ADM Athlon dual core chip. 

in dmesg, I see that etho is loaded, and that my NIC is: Broadcom 4400 10/100BaseT.

If I type ifconfig, I see eth0, however I do not have an IP address.  I can statically set it, but I still connot see anything. 

From my research, it has successfully loaded the b44 driver.  I can tell because the I can see eth0 when running ifconfig.  I'm not sure what to do next!

On a side note, if I install the x86 version on the AMD computer, networking works just fine.  Can anyone offer pointers regarding how to troubleshoot this problem?  I would appreciate any help I can get!

---

### Post by lloyd_b on 2006-12-08
Could you post the contents of your "/etc/network/interfaces" file?  

Another question:  Are you expecting DHCP to set the IP address (and other network options), or are planning on using static IP's?

Finally: Could you run the following command, and post the output:

```
sudo /etc/init.d/networking restart
```

This will stop and restart the network subsystem (and hopefully provide some messages that will help diagnose what's going on).

My guess is that your machine is configured for DHCP, but there's no DHCP server to provide it with an IP.  Statically setting the IP via ifconfig is a start, but you'd also need to set the proper routes and DNS in order to have a working network connection.

Lloyd B.

---

### Post by kwilliams0 on 2006-12-08
Lloyd,

First off, thanks for the response.  

You are right in that I do expect DHCP to set the IP address.  I know I have a working DHCP server (m0n0wall) as I have other windows boxes running against it, and I can connect to the internet using the x86 installation CD (using DHCP.)  Everything is plugged into a Linksys Switch--and I tried switching to a different cable that I know worked as well.

When I tried a restart, it stated:

* Reconfiguring network interfaces...
SIOCDELRT: No such process
Internet Systems Consortium DHCP Client v.3.0.3
Copyright 2004-2005 Internet Systems Consortium
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: NO such device
Failed to bring up eth1.

I get the same thing for eth2, ath0, and wlan0 as I did for eth1.  I only have 1 NIC, so I don't even know why eth1, eth2, atho0, and wlan0 are there (are what was detected to make them present during the installation).

To clean everything up, I changed my /etc/network/interfaces file to only contain (it had eth1, eth2, auth0, and wlan0):

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

I then did /etc/init.d/networking stop and it seemed to stop ok.

I then did /etc/init.d/networking start and got the following:
 * Configuring network interfaces
Internal Systems Consortium DHCP Cleint...(legal stuff)
Listening on LPF/eth0/00:18:8b:74:a6:26
Sending on LPF/eth0/00:18:8b:74:a6:26
Sending on Socket/Fallback
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 8
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 8
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 14
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 8
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 14
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 9
No DHCPOFFERS received
No working leases in persistent database - sleeping.

So, to rule out DHCP, I set it to static IP as follows:
ifconfig eth0 192.168.1.8
ifconfig eth0 netmask 255.255.255.0
ifconfig eth0 broadcast 192.168.1.1
route add default gw 172.30.49.1 (got an error here, SIOCADDRT: Network is unreachable)

I didn't worry about DNS yet, as I can't ping my gateway.

I'm out of my realm at this point, so any more pointers would be GREATLY appreciated! (Thanks agian Lloyd for the response)

---

### Post by ColdCanuck on 2006-12-08
That broadcast addr looks a little suspect. 

I would set it to 192.168.1.255. 

What does an the output of ifconfig look like after you have hand configured the interface.

---

### Post by lloyd_b on 2006-12-08
```
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 8
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 8
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 14
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 8
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 14
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 9
No DHCPOFFERS received
No working leases in persistent database - sleeping.
```

Indicates that it isn't finding a DHCP server.  No surprise there.

> So, to rule out DHCP, I set it to static IP as follows:
ifconfig eth0 192.168.1.8
ifconfig eth0 netmask 255.255.255.0
ifconfig eth0 broadcast 192.168.1.1
route add default gw 172.30.49.1 (got an error here, SIOCADDRT: Network is unreachable)

First off - an assumption.  I'm assuming this is a home network, and that you're connecting to the internet via a DSL or Cable modem/router.  If that assumption is wrong, then the following advice is of limited value.

Ok - eth0 is being defined as 192.168.1.8.  With a netmask of 255.255.255.0, that means that eth0 can directly reach any computer with an  address of 192.168.1.x.  To get to any address outside of that range, you have to go through a gateway. However, you're attempting to connect to a gateway at 172.30.41.1, which is outside of that range.  That's why you're getting the "Network is unreachable" - you haven't told it the gateway to use to reach that address.

The "broadcast" address is wrong.  Broadcast addresses are at x.x.x.255 (though I've seen references to x.x.x.0 for broadcast).

What I *suspect* is that your gateway should be at 192.168.1.1, and the broadcast address at 192.168.1.255.  I believe this because gateways are generally assigned to x.x.x.1 addresses.

Are you sure that your gateway is at 172.30.41.1?  If you're using a DSL/Cable Modem, then most likely it's doing NAT (Network Address Translation), and that's a believable IP for it's *external* address.  The *internal* address (the address as seen by your computers) is most likely 192.168.1.1.

So try this:

```
sudo ifconfig eth0 192.168.1.8 netmask 255.255.255.0 broadcast 192.168.1.255
sudo route add default gw 192.168.1.1

```

(Note that you can pile the IP, netmask, and broadcast address all onto a single command).

At that point, you should be able to ping 192.168.1.1.  And if I'm right about that being the correct address for the gateway, then you should be able to ping to an external IP (try 209.191.93.52 ([www.yahoo.com](www.yahoo.com)) or 82.211.81.186 ([www.ubuntuforums.org))](www.ubuntuforums.org))). 

If this works, then you've got a working connection, minus DNS. 

If this works, it will be relatively easy to configure you machine with a static IP (at least until you can sort out the DHCP issues).  In "/etc/network/interfaces":

```
auto eth0
iface eth0 inet dhcp
```

to 

```
auto eth0
iface eth0 inet static
     address 192.168.1.8
     netmask 255.255.255.0
     broadcast 192.168.1.255
     gateway 192.168.1.1
```
     

I've seen a reference to adding a nameserver in here as well, but I can't remember what it is (and it's not documented in the man page).  You can manually add a nameserver by editing "/etc/resolv.conf", and adding one or more "namesever x.x.x.x" lines (where the x's are the IP address for the nameserver.  If you don't know what your nameserver's IP address is, try "nameserver 192.168.1.1" - a lot of DSL/Cable modems also act as proxies for the ISP's DNS.

As for the DHCP - I'm not really that familiar with it, but those messages don't look quite right. Specifically:

```
DHCPDISCOVER on etho0 to 255.255.255.255. port 67 interval 8
```

What the heck is "etho0".  I *think* it should be "eth0".  I'm not sure where this is controlled...

Lloyd B.

---

### Post by kwilliams0 on 2006-12-09
Thanks again for the answers!

Your assumption that this is on my home network using DSL is correct.

I had a typo with the etho0, as I can't send this stuff over the network, I am manually typing everything onto a working computer on my network.

Apparently I was a little sloppy regarding networking as well, so I folllowed your recommendations (all your assumptions are correct, and nice catch on the dump gateway move).  I was able to add the default gateway as well.

Now when I enter ifconfig, I see:
```
eth0:
Link encap:Ethernet HWaddr 00:18:88:74:A6:26
inet addr: 192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
inet6 addr: fe80...
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:869 errors:0 dropped:863 overruns:0 frame:0
TX packets:2395 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:118934 (116.1KiB) TX bytes:554542 (541.5 KiB)

lo:
Link encap: Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
...
```

When I enter route I see:
192.168.1.0		*		255.255.255.0	U 	0	0	0	eth0
default		192.168.1.1	0.0.0.0			UG	0	0	0	eth0


so everything seems to be right...

So when I ping 192.168.1.1, I get:
```
From 192.168.1.8 icmp_seq=2 Destination Host Unreachable.
From 192.168.1.8 icmp_seq=3 Destination Host Unreachable.
From 192.168.1.8 icmp_seq=4 Destination Host Unreachable.
From 192.168.1.8 icmp_seq=5 Destination Host Unreachable.
```

If it weren't for the fact that I can connect to the network on this machine when I am running the x86 ubuntu dapper drake CD, I would swear I have a bad cable--but since I can it has to be something on the computer.  Do you have any other ideas?

---

### Post by lloyd_b on 2006-12-09
The ifconfig and route outputs look right.

"Destination host unreachable" means that there was no response from the machine.  Which means:

1.  Cable issue.

2.  Problem with the device driver for the Broadcom.

3.  Your gateway ISN'T at 192.168.1.1

#1 - Ruled out by the fact that you've got network connectivity with the Live-CD.

#2 - Same as #1.  It works from the Live-CD.  Just for a double-check, I did a quick search in the forums for that device, and came up with nothing relevant.

Which leaves #3.  I *assumed* that your gateway would be at 192.168.1.1 because you're using 192.168.1.x addresses.  That doesn't necessarily make it so (for example, my DSL modem is at 192.168.0.1, so my home network uses the 192.168.0.x network).

> If it weren't for the fact that I can connect to the network on this machine when I am running the x86 ubuntu dapper drake CD, I would swear I have a bad cable--but since I can it has to be something on the computer. Do you have any other ideas?

One that jumps out at me - start up the machine from that CD, then run the "ifconfig" and "route" commands from there.  Let's see what values for IP and gateway are being assigned from the *working* version...

Lloyd B.

---

### Post by kwilliams0 on 2006-12-09
OK, I ran the ifconig and route commands on the booted CD.  First, it grabbed the IP address from my DHCP server.  The gateway is 192.168.1.1, and the ifconfig is

net addr: 192.168.1.197  Bcast:192.168.1.255  Mask:255.255.255.0

Could this be a corrupted module as it is compiled for the amd64 and not the x86?  Maybe I should try installing the module from the x86 disk?  Do you think that would work (I'm out of my realm on that stuff, but will learn--any pointers are appreciated though!)

I did read that this machine is having issues due to eth0 and usb drives sharing a IRQ, but I looked in /proc/interrupts, and mine wasn't:
58: 14 0 IO-APIC-level eth0

---

### Post by lloyd_b on 2006-12-09
So it appears that it *is* a driver issue after all - the 64bit driver for the Broadcom doesn't work (while the 32bit driver for said device does).

I honestly have no clue whether or not you can use an x86 driver with that kernel.  

Lloyd B.

---

### Post by kwilliams0 on 2006-12-09
OK, 

That's what I am thinking too, so it's good to be validated.  Thanks again for the help.  I have one final question.

I have purchased a Netgeer Gigabit (GA311) from, and I now have internet access--I appear to be up and running now!

Thanks again for your assistance in helping me troubleshoot this problem, I really appreciate it!

I might spend some time continuing to try and troubleshoot this problem (install the AMD specific kernel, instead of the generic 64 bit one, and try to self compile the module as well).  If I have any luck, I'll post it here in hopes that it might help someone else :)

---

