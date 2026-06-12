---
title: "Ethernet connection not working"
date: 2009-01-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by davideotape on 2009-01-19
After upgrading from 8.10 to 9.04 alpha3, my Ethernet connection to the internet has stopped working. It has worked fine on every OS I have used previously, so I am forced to conclude that there is something wrong with either network manager or Ubuntu. I have checked that no firewall is running in the background, and the little tray icon claims to be connected. However, when I open up either Firefox, Ephiphany, Opera, or Update Manager, all of them say I am not connected to the internet.

All help appreciated :)

David

---

### Post by superprash2003 on 2009-01-19
go to the terminal and type ifconfig and post output

---

### Post by davideotape on 2009-01-19
Here is the output for ifconfig:

```
david@david-desktop:~$ sudo ifconfig
[sudo] password for david: 
eth0      Link encap:Ethernet  HWaddr 00:1a:92:5d:75:b2  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe5d:75b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2681 (2.6 KB)  TX bytes:5142 (5.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3420 (3.4 KB)  TX bytes:3420 (3.4 KB)

david@david-desktop:~$ 

```

---

### Post by Rocket2DMn on 2009-01-19
Moved to Jaunty Jackalope Testing and Discussion.

---

### Post by jfernyhough on 2009-01-19
You have an IP address which would suggest your network and the network card are working fine

Have you checked your proxy settings?

What does route output?

---

### Post by davideotape on 2009-01-19
> **jfernyhough said:**
> Have you checked your proxy settings?

What does route output?

How do I do this?

Sorry, I don't know much about networking.

---

### Post by inportb on 2009-01-19
> **davideotape said:**
> [QUOTE=jfernyhough;6579240]What does route output?How do I do this?

Sorry, I don't know much about networking.[/QUOTE]

Try typing route ;p

---

### Post by davideotape on 2009-01-19
Here is the output from route:

```
david@david-desktop:~$ sudo route
[sudo] password for david: 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
david@david-desktop:~$ 
```

EDIT:

> **inportb said:**
> Try typing route ;p

Thank you inportb for pointing out the blindingly obvious to me. I not having the best of days today.

---

### Post by jfernyhough on 2009-01-19
OK, eth0 is not picking up a gateway, so while it's active it doesn't know how to get out of your local network. :)

It should look like:
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.254   0.0.0.0         UG    0      0        0 wlan0
```

Note the G on 192.168.0.254.

Sounds like the network-manager settings need a kick. Try right-clicking on the network-manager applet, edit connections, Wired, select Auto eth0, Delete.

We now need to get network manager to redetect the connection. This could be a number of ways. A simple restart is easiest, or $ sudo /etc/init.d/network-manager restart.

---

### Post by minisori on 2009-01-19
I had this problem too after the update. I had to add the 2 last lines to /etc/network/interfaces


> auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp


The problem is that now network manager can't control it.

---

### Post by davideotape on 2009-01-19
> **jfernyhough said:**
> 

Sounds like the network-manager settings need a kick. Try right-clicking on the network-manager applet, edit connections, Wired, select Auto eth0, Delete.

We now need to get network manager to redetect the connection. This could be a number of ways. A simple restart is easiest, or $ sudo /etc/init.d/network-manager restart.

Okay, tried to delete the connection but get this message:

Removing connection failed: nm-settings.c.333 - Read-only connections may not be deleted.

---

### Post by jfernyhough on 2009-01-19
OK, let's go hardcore. :)

Well, maybe not hardcore. But more hardcore than using a GUI. :D

Log out, switch to a console (CTRL-ALT-F1) and log in.

$ rm -fR .gconf/system/networking/connections

This will delete all the data GNOME has about any connections and will reset back to defaults.

To be on the safe side, I'd reboot, log in on a console again and check the directory is still empty. It should be, but gconf is an odd beastie.

When you log into GNOME (CTRL0ALT-F7 to get back to GDM) network manager should redetect the network and configure it correctly.

(There's probably a more correct way of doing this using gconftool but this way worked for me previously when NM was upgraded from 0.6 to 0.7)

---

### Post by davideotape on 2009-01-19
Okay, I have followed those instructions, resarted, and it isn't connecting for me, claiming that "device is unmanaged"

---

### Post by jfernyhough on 2009-01-19
OK,

$ sudo gedit /etc/network/interfaces

Make sure there is no reference to eth0 or anything other than lo, i.e.:

```
auto lo
iface lo inet loopback
```

---

### Post by ShirishAg75 on 2009-01-19
I also have an Ethernet connection but its an Ethernet connection to the router/modem. 

My route output is a little bit different. 

```

~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         mygateway1.ar7  0.0.0.0         UG    0      0        0 eth1


```

---

### Post by davideotape on 2009-01-20
> **ShirishAg75 said:**
> I also have an Ethernet connection but its an Ethernet connection to the router/modem. 

Mine is connecting to a router too. I doubt you have a modem, as those are only used for dial-up connections to my knowledge.

I have taken all the steps you have told me to jfernyhough, but to no avail. I seem to have gone round in a circle, and have returned back at the start. Here are my current outputs for:

**_ifconfig:_**

```
david@david-desktop:~$ sudo ifconfig
[sudo] password for david: 
eth0      Link encap:Ethernet  HWaddr 00:1a:92:5d:75:b2  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe5d:75b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7175 (7.1 KB)  TX bytes:10029 (10.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3328 (3.3 KB)  TX bytes:3328 (3.3 KB)

```

**_route:_**

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
david@david-desktop:~$ 
```

---

### Post by ShirishAg75 on 2009-01-20
you might be hitting some dns issue. What does nslookup give you?

This is on my system (running Intrepid atm but should be similar output on Jaunty)

```


$ nslookup google.com
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    google.com
Address: 72.14.205.100
Name:    google.com
Address: 74.125.45.100
Name:    google.com
Address: 209.85.171.100


```

One another thing you could try is :-

```
$ sudo dhcpclient 
```

you could do a "man dhcpclient3" if you want to know what it is. 

Give output of that as well. 

thing try to ping some IP. 

Something like 

```

$ ping -c 5 72.14.205.100
PING 72.14.205.100 (72.14.205.100) 56(84) bytes of data.
64 bytes from 72.14.205.100: icmp_seq=1 ttl=240 time=301 ms
64 bytes from 72.14.205.100: icmp_seq=2 ttl=240 time=300 ms
64 bytes from 72.14.205.100: icmp_seq=3 ttl=240 time=302 ms
64 bytes from 72.14.205.100: icmp_seq=4 ttl=240 time=303 ms
64 bytes from 72.14.205.100: icmp_seq=5 ttl=240 time=301 ms

--- 72.14.205.100 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4015ms
rtt min/avg/max/mdev = 300.462/301.710/303.588/1.092 ms


```


at my end . 

```


$ ping -c 5 google.com
PING google.com (209.85.171.100) 56(84) bytes of data.
64 bytes from google.com (209.85.171.100): icmp_seq=1 ttl=237 time=351 ms
64 bytes from google.com (209.85.171.100): icmp_seq=2 ttl=237 time=350 ms
64 bytes from google.com (209.85.171.100): icmp_seq=3 ttl=237 time=349 ms
64 bytes from google.com (209.85.171.100): icmp_seq=4 ttl=237 time=348 ms
64 bytes from google.com (209.85.171.100): icmp_seq=5 ttl=237 time=349 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4015ms
rtt min/avg/max/mdev = 348.853/349.903/351.840/1.166 ms


```

---

### Post by jfernyhough on 2009-01-20
I think I may have it...

Right-click on the icon, Edit Connections, edit Auto eth0.

IPv4 Settings, make sure Automatic (DHCP) is set. Click on Routes. If "Ignore..." is ticked, untick it. If unticked, tick it. OK out, reconnect to the network.

---

### Post by Gina on 2009-01-20
Yes, it sounds like DHCP trouble.  I had problems in Ubuntu with wireless networking a while back but not with ethernet.  Generally Ubuntu seems much better at setting up networking automatically these days.

---

### Post by davideotape on 2009-01-21
First of all, here are some outputs that ShirishAg75 asked me to run:

```
$ nslookup google.com
Server:		192.168.1.254
Address:	192.168.1.254#53

Non-authoritative answer:
Name:	google.com
Address: 74.125.45.100
Name:	google.com
Address: 209.85.171.100
Name:	google.com
Address: 72.14.205.100
```

```
$ man dhcpclient3
No manual entry for dhcpclient3
```

```
$ ping -c 5 google.com
connect: Network is unreachable
```

In reply to jfernyhough, I am sorry to report that I am not able to edit the network connections. I try to edit eth0, but all I get is a greyed out box, that doesn't allow me to edit any of the settings.

Thanks to everyone who is trying to help, and I hope that my problem gets fixed soon.. ;)

---

### Post by taavikko on 2009-01-21
Just a thought, do you use somekind of an firewall?
firestarter, ufw, or directly iptables/netfilter...

If firestarter disable it. that's known to cause problems.

If ufw: **sudo ufw status**

If iptables: **sudo iptables -L**

---

### Post by davideotape on 2009-01-21
> **taavikko said:**
> Just a thought, do you use somekind of an firewall?

Yes, I have installed lokkit, but I have checked under running processes and it doesn't appear there. I have had no problems with it in the past though...

---

### Post by taavikko on 2009-01-21
> **davideotape said:**
> Yes, I have installed lokkit, but I have checked under running processes and it doesn't appear there. I have had no problems with it in the past though...

Never heard, but i'll suspect it writes it settings in iptables,
And since jaunty is in alpha state, b0rkage may happen...

so check it's status: **sudo iptables -L**

---

### Post by davideotape on 2009-01-21
Okalydokaly, here's the output for iptables:

```
$ sudo iptables -L
[sudo] password for david: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
RH-Lokkit-0-50-INPUT  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
RH-Lokkit-0-50-INPUT  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain RH-Lokkit-0-50-INPUT (2 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  BThomehub.home       anywhere            udp spt:domain 
REJECT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp reject-with icmp-port-unreachable 

```

I don't have a clue what any of that means though :S

---

### Post by marmuta on 2009-01-22
Well, for some reason the default gateway is missing from your routing table. Since Gina already mentioned dhclient, there is [[jaunty] option rfc3442-classless-static-routes causes missing routes]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204"). People there have the same symptoms and suspiciously the same router ip 192.168.1.254 and they found a workaround.
[QUOTE=Bogdan Butnaru]# Now I commented-out the rfc3442 option in dhclient.conf
$ grep rfc3442 /etc/dhcp3/dhclient.conf
#option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;
# rfc3442-classless-static-routes;
[/QUOTE]
Basically run ```
sudo gedit /etc/dhcp3/dhclient.conf
``` and comment out ( put '#' in front of) the two lines containing 'rfc3442' and restart. There is more in the bug report if it doesn't work the first try.
Hope that helps.

---

### Post by davideotape on 2009-01-22
> **marmuta said:**
> Basically run ```
sudo gedit /etc/dhcp3/dhclient.conf
``` and comment out ( put '#' in front of) the two lines containing 'rfc3442' and restart. There is more in the bug report if it doesn't work the first try.
Hope that helps.

Thankyou

That worked a treat. Now I have my internet back :D

I do still have two questions though.

1. What happened to the thanks button on the forums?

and

2. How do I mark the thread as solved?

---

### Post by oooh on 2009-01-23
Same problem here on:

Hardy on Sony Vaio FZ21M

No internet here. I can ping other computers in the network, but NOT the gateway. I use static. I made no cable/router config changes (I did change from DHCP to static some weeks ago, and I had internet w/o problem). 

My routing table: route -vn
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
127.0.0.0       0.0.0.0         255.0.0.0       U         0 0          0 lo
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

I do not like this 169.254.0.0 that I get, and I do not know where it comes from or how to delete it. System does not let memodify the route file, or delete this line.

My /etc/network/interfaces has got the auto lo and the auto eth0. However it is completely messy, with a lot of line returns and empty lines and the auto eth0 at the end of the file (?!?!?! weird)

I can even ping other computers in the network, but not the gateway. I can not ping the outside world, neither IP addresses or domain names.

I set the my hostname to be the same as the hosts entry for 127.0.1.1. This solved a start up problem and system works faster now (nautilus starts faster, terminal sudo prompts for password faster). 

So questions are:
- How do I modify my routing table? Is this 169.254.0.0 wrong?
- How to completelly unload Firestarter?
- How to completelly disable iptables?

I hope you can help me ... I have no dual boot (brave guy, I know) and this is driving me nuts.

---

### Post by Lutin on 2009-01-23
> **davideotape said:**
> TI do still have two questions though.

1. What happened to the thanks button on the forums?

and

2. How do I mark the thread as solved?


These functions have been temporarily suspended, apparently.

They should be back after the gremlins have been tracked down.

---

### Post by marmuta on 2009-01-24
> **oooh said:**
> 
No internet here. I can ping other computers in the network, but NOT the gateway. I use static. I made no cable/router config changes (I did change from DHCP to static some weeks ago, and I had internet w/o problem). 

Mhmm ... weird, are you sure 192.168.1.1 is your routers ip, not maybe 192.168.2.1?
This should list everything on your network:
```
arp -an
```
Else, please also post the output of 
```
ifconfig -v -a
sudo iptables-save
sudo dhclient eth0
ifconfig -v -a # (again)

```
> - How do I modify my routing table?
Check out "man route" or "man ip".
The lazy way to delete a route manually is
```
ip route show
...         
sudo ip route del <copy&paste any line from above output>

```

> Is this 169.254.0.0 wrong?
No, should be fine. That's for link local routing. Avahi adds that but AFAIK it's just a kind of fallback in case there is no other (routable) ip on eth0.
> - How to completelly unload Firestarter?
I've hardly ever used it but I guess uninstalling it would do. Of course the actual firewall is iptables. Better look at that one first, see below.
> - How to completelly disable iptables?
```
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT

```

---

### Post by marmuta on 2009-01-24
> **davideotape said:**
> Thankyou

That worked a treat. Now I have my internet back :D

Great, I'm glad it worked.

I've fiddled around with that bug a little, trying to reproduce it, but no luck so far. Could you please have a look at my post in the [bug report]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204") and see if you can add that tcpdump output?

---

### Post by oooh on 2009-01-26
Thanks marmuta for the detailed answer:

The weirdest thing ever happened today. After a weekend not using the laptop, now internet goes fine again. Route table looks fine as well. I did not touch the network, nor the laptop, and I think no update or whatever was done in my system router or whatever.

I am NOT a newbie on networks, but this makes no sense to me. A cable thingy? maybe a problem in the hub? maybe abother computers collapsing the network ? maybe a safety issue ?

Maybe the firestarter was restarted and is not interfering now my system. I associated it once to ethernet, and the last time, before the last restart I associated it to wlan0. So maybe only after restart the changes are effective and firestarter is no longer blocking my network ethernet interface. Anyhow, even if it was locked before to ethernet, I had it set OFF. So this is the most sensible explanation I can find. Any suggestions ?

Anyway, here comes all the info you requested:
- arp -an
? (192.168.1.1) en 00:14:BF:9F:16:A0 [ether] en eth0

-  ifconfig  -v -a
eth0      Link encap:Ethernet  direcciónHW 00:1a:80:23:1d:db  
          inet dirección:192.168.1.104  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::21a:80ff:fe23:1ddb/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:106886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183705 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:43709495 (41.6 MB)  TX bytes:70654433 (67.3 MB)
          Interrupción:16 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:55044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55044 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:1639242 (1.5 MB)  TX bytes:1639242 (1.5 MB)

wlan0     Link encap:Ethernet  direcciónHW 00:1d:e0:19:15:3b  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  direcciónHW 00-1D-E0-19-15-3B-00-00-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

- sudo iptables-save
# Generated by iptables-save v1.3.8 on Tue Jan 27 00:48:45 2009
*nat
:PREROUTING ACCEPT [940:63932]
:POSTROUTING ACCEPT [4925:347643]
:OUTPUT ACCEPT [4925:347643]
COMMIT
# Completed on Tue Jan 27 00:48:45 2009
# Generated by iptables-save v1.3.8 on Tue Jan 27 00:48:45 2009
*mangle
:PREROUTING ACCEPT [160166:45216517]
:INPUT ACCEPT [160166:45216517]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [238749:69726110]
:POSTROUTING ACCEPT [238899:69751738]
COMMIT
# Completed on Tue Jan 27 00:48:45 2009
# Generated by iptables-save v1.3.8 on Tue Jan 27 00:48:45 2009
*filter
:INPUT ACCEPT [160166:45216517]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [238749:69726110]
COMMIT
# Completed on Tue Jan 27 00:48:45 2009

- sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:80:23:1d:db
Sending on   LPF/eth0/00:1a:80:23:1d:db
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

- ifconfig -v -a # (again)
eth0      Link encap:Ethernet  direcciónHW 00:1a:80:23:1d:db  
          dirección inet6: fe80::21a:80ff:fe23:1ddb/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:106945 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183771 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:43724464 (41.6 MB)  TX bytes:70665249 (67.3 MB)
          Interrupción:16 

eth0:avahi Link encap:Ethernet  direcciónHW 00:1a:80:23:1d:db  
          inet dirección:169.254.6.63  Difusión:169.254.255.255  Máscara:255.255.0.0
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          Interrupción:16 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:55051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55051 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:1639858 (1.5 MB)  TX bytes:1639858 (1.5 MB)

wlan0     Link encap:Ethernet  direcciónHW 00:1d:e0:19:15:3b  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  direcciónHW 00-1D-E0-19-15-3B-00-00-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

After I did the dchlient on eth0 (i use static ip) I lost internet again. Then I did arp -an again and the avahi (169.254.6.63) was there again. I restarted the network interfaces and then internet came back again. No clue ... really any ideas welcome ...

---

### Post by marmuta on 2009-01-26
Did you power-cycle the gateway/router over the weekend? Maybe it crashed before, with the switch/hub still partly working. At least I don't see any other road blocks from the info. 
Anyways, good to hear it works now.

---

### Post by oooh on 2009-01-27
Probably the gateway was restarted on the weekend.

However, when I had no internet, the rest of my house mates (4 people) had internet.

Anyway, if it happens again, I will dump here all the details again.

Thanks again

---

