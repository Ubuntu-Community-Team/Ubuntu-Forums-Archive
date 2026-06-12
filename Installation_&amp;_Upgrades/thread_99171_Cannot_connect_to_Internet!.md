---
title: "Cannot connect to Internet!"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by FourBrane on 2005-12-05
I'm posting this under Windoze XP from the same machine on which I have installed Ubunto 5.10 but which, alas, cannot reach the outside world.

Under Ubuntu, I can ping 192.168.1.1 and other boxes on my LAN. However, if I ping a bare IP address outside the LAN, I get...
From 192.168.1.1 icmp_seq=1 Destination Net Unreachable. 
Because of that failure, DNS cannot resolve anything even though /etc/resolv.conf has the full list of correct DNS hosts twhich were acquired somehow.

I don't think my problem is specific to Ubuntu, as Knoppix and SuZE both failed to get connected. So, maybe there's something inherently unlinuxy in my setup.

Here are the particulars.

Machine is an Acer Aspire 1690 laptop with both wireless (Broadcom NetXtreme Gigabit) and 10/100 NIC. The wireless internet works (at least, it did for me when I used it once), but I _DON"T WANT_ to use wireless right now as this is a home office and I've got a perfectly good, more secure ethernet cable right here.

My ethernet cable runs to a 4-port Linksys BEFSR41 V3 (with original software) being used as a hub handling two computers connected to a 4-port Linksys BEFW11S4 V2 router (with wireless disabled, DHCP turned on, and software upgraded to latest release) which services the hub plus two other computers. The router runs out to an Linksys Etherfast cable modem. 

Here are my relevant dmesg lines:

[21.910115] eth0: Tigon3 [partno(BCM95705A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:c0:9f:99:c0:e1
[21.910122] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[0] TSOcap[1] 
[21.910125] eth0: dma_rwctrl[763f0000]
[53.572095] tg3: eth1: Link is up at 100 Mbps, full duplex.
[53.572098] tg3: eth1: Flow control is on for TX and on for RX.

I modified /etc/modprobe.d/aliases to disable Ipv6 with 'net-pf-10 off' because these are older Linksys boxes which only speak Ipv4. 

My /etc/network/interfaces contains:
auto lo
iface lo inet loopback
mapping hotplug
	script grep
	map eth1
iface eth1 inet dhcp
auto eth1
iface eth0 inet dhcp

ifconfig reports:
eth1      Link encap:Ethernet  HWaddr 00:C0:9F:99:C0:E1  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4873 (4.7 KiB)  TX bytes:3108 (3.0 KiB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:256630 (250.6 KiB)  TX bytes:256630 (250.6 KiB)


When I invoke route, the program takes a looooooooong time and comes back with nothing but this:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

I think the routing is probably the trouble, but I simply don't know enough to know what tools to use or how to go about fixing the routing so it boots up with routing set properly each time (under dhcp).

Does anyone recognize the problem?

I much appreciate your help.

---

### Post by wbiggers on 2005-12-05
I had lots of problems using DHCP and switched my systems to static IP addresses.  Also, don't use your local router/gateway for a DNS server.  If you can, go into the router/gateway configuration and see what it uses for a DNS server.  Then, go to System>Networking and manually enter those DNS Server addresses on the DNS tab.  While you are there, change the interfaces to static IP addresses inside your subnet (192.168.1.x).  If you leave them as DHCP, it will overwrite the DNS entries you just made.

---

### Post by FourBrane on 2005-12-13
I have finally discovered and resolved the source of my trouble. I am posting this  in hopes of reducing someone else's pain.

To recap, I had a Linksys router being used as a hub (no use of "internet" port, with port 4 connected to one of the ports on another Linksys router where the actual connection to the internet occured).

I assumed that the "hub" router would not be answering any dhcp requests or even responding to its own address. This assumption seemed to be correct because Windoze could reach the 'net and if I entered [http://192.168.1.1](http://192.168.1.1) I got the password request and menu for the far-distant router. The only way I could reach the menu for the near router was to unplug port 4.

THIS ASSUMPTION WAS WRONG.

As soon as I changed the address of the "near" router to something which would not conflict (and turned off dhcp on that router), Ubuntu (or any Linux) could suddenly see the internet!

So, if you're experiencing symptoms like mine, check for address conflicts between the two routers, even though one is only being used as a hub.

DHCP now works perfectly under Ubuntu (I prefer to use DHCP since it simplifies pulling boxes on and off the LAN, something I do more than most people would be doing).

---

