---
title: "YAVPNP (yet another VPN problem)"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by dott.malcom on 2005-05-29
Hi all,

finally I was able to install pptp and pptpconfig
- [http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/) -

After some attempt i was able also to connect! Wow! but the connection doesn't work (maybe routing problem?)

The situation is now as follows:

1) I can connect but if I try to load pages in firefox i'm not able to load any

2) This is the output of **ifconfig**  and **route** after the connection
malcom@Assapan:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:4F:F9:63
          inet addr:172.16.70.120  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe4f:f963/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:521242 (509.0 KiB)  TX bytes:149917 (146.4 KiB)
          Interrupt:20 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14475317 (13.8 MiB)  TX bytes:14475317 (13.8 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:157.193.1.48  P-t-P:157.193.46.4  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:111 (111.0 b)  TX bytes:80632305 (76.8 MiB)

malcom@Assapan:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
157.193.46.4    *               255.255.255.255 UH    0      0        0 ppp0
172.16.70.0     *               255.255.255.0   U     0      0        0 eth0
default         172.16.70.254   0.0.0.0         UG    0      0        0 eth0

3) I'm in a University net so i get my IP with DHCP and (i think the cause of this is DHCP) after few minutes of connection if you type again **route** there is no *ppp0* anymore.

Can you please help me, i don't know what else i can do
thank you all in advance

DM

---

### Post by dott.malcom on 2005-05-29
trying to keep it up....

---

### Post by dott.malcom on 2005-05-30
nobody knows.... up!

---

### Post by cwaldbieser on 2005-05-30
Well, I am not sure what could be causing the connection to drop-- you will probably have to talk to your university about that.  Your routing table looks a little fishy to me, though.

You have three line in the routing table when you connect, and I am interpreting them as saying the following:

1) If I am trying to send a (TCP/IP) message to address 157.193.46.4, send it over my ppp0 device.

2) If I am trying to send a message to address to the 172.16.70.* network, send it over device eth0 (your ethernet card).

3) If I am trying to send a message anywhere else besides #1 and #2, send it to device eth0 (the ethernet card, again).

So you can see, if you are trying to send a message over the VPN, that will only happen if the message is explicitly to a machine with the IP address 157.193.46.4.  That seems a little weird to me.  When I connect to my VPN at work, I basically have access to an entire subnet.  Also, the address your ppp0 device was given is 157.193.1.48.  The machine you are connection to on the remote side of the VPN is address 157.193.46.4.  I am guessing you should probably do:

```
$ sudo route add 157.193.0.0 netmask 255.255.0.0 dev ppp0
```

That should add a rule that says, whenever I am trying to send a message to any machine on the 157.193.*.* network, send it over my ppp0 device.

As far as the web browser not working, try doing a traceroute to the site you are trying to bring up.  E.g.

```
$ traceroute www.yahoo.com
```

This should show you roughly what machines the message is being sent over.  If something looks funny (message is not being sent to the right machines), then you can figure out what's wrong based on that.

Another thing to try is to find someone who actually does have a working VPN connection, and look at their settings.  With UNIX systems, you can just use ifconfig and route.  On Windows, you can use "ipconfig" and "route print" in the console box.

Hope that helps.

---

### Post by dott.malcom on 2005-05-30
In PPTPconfig there are some box you can check that creates different rules in the routing table automatically:
1 - Client to Server
2 - Client to LAN
3 - LAN to LAN
4 - all to tunnel

I keep the first one because in that case i'm able to ping the server.

---

### Post by dott.malcom on 2005-05-30
really thank you, it helps anyway because now i've understand how to use traceroute and also the command under windows "route print" thanks you, i'll continue trying and if i got something new i'll tell you.

Anyway I think that my vpn server give me a 157. address that let me access the 172.x gateway (LAN has 172 IPs and VPN has 157. IPs)

---

### Post by dott.malcom on 2005-05-31
I found out that my problem is routing for sure, and is a "looping" problem.
here shoud be the solutions:

[http://pptpclient.sourceforge.net/howto-diagnosis.phtml#ip_loop](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#ip_loop)

I think tha my situation best fits "point 4"

> 4. the PPTP Server may have given its own IP address for the new interface (compare "remote IP address" in the debug logs with the IP address you give to pptp).

But I don't know how to do answer *"c"* and *"d"*

c:
request a more appropriate address by adding an option such as :10.0.1.1, where 10.0.1.1 is the address to be adopted
d:
use the iptables and ip commands to direct the tunnel packets away from the tunnel interface

Can you help me with this?

---

### Post by dott.malcom on 2005-05-31
So, i'v done point a) and b) but the problem still remain, the traffic is looped.  ](*,)    :cry:

I'm not able to do more, I need help, please!

*Here is the output of ifconfig and route before and after tunnel:* 
> 
###########BEFORE TUNNEL
malcom@Assapan:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:4F:F9:63
          inet addr:172.16.70.120  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe4f:f963/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1043 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2154909 (2.0 MiB)  TX bytes:136322 (133.1 KiB)
          Interrupt:20 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17178725 (16.3 MiB)  TX bytes:17178725 (16.3 MiB)

malcom@Assapan:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.70.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         172.16.70.254   0.0.0.0         UG    0      0        0 eth0


##########AFTER TUNNEL
malcom@Assapan:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:4F:F9:63
          inet addr:172.16.70.120  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe4f:f963/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1067 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2176209 (2.0 MiB)  TX bytes:138350 (135.1 KiB)
          Interrupt:20 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17427193 (16.6 MiB)  TX bytes:17427193 (16.6 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:157.193.29.10  P-t-P:157.193.46.4  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:111 (111.0 b)  TX bytes:24623569 (23.4 MiB)


malcom@Assapan:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
157.193.46.4    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
172.16.70.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         172.16.70.254   0.0.0.0         UG    0      0        0 eth0


*And here the script that concern point a) and b) of the solution:*

> 
sudo ifconfig ppp0 pointopoint 172.16.70.120
sudo route add -host 157.193.46.4 gw 172.16.70.254 dev ppp0

where 172.16.70.120 is my internal LAN address (you can see from ifconfig)

At the end my problem is always the same:
traffic loop
i'm not able to ping the VPN server
157 VPN server and 172.16.70.254 the gateway that is supposed to be the door to internet.

---

### Post by dott.malcom on 2005-06-02
up!

---

### Post by BeeZ on 2005-06-02
[QUOTE=dott.malcom]up![/QUOTE]
 gj :)

---

### Post by alastair on 2005-06-02
Look in the logs and see what happens - before,during and after the connection i.e.

Open a shell and :

sudo tail -f /var/log/syslog

Connect .... check logs

See if anything odd happens.

---

