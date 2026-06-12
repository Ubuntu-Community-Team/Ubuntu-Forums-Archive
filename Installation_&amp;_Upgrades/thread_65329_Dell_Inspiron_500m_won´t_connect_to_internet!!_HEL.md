---
title: "Dell Inspiron 500m won´t connect to internet!! HELP!?!?"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by andrenos on 2005-09-13
I´ve just installed Ubuntu on my Dell Inspiron 500m laptop. But it won´t connect to internet!!
In this laptop it´s a wireless ethernet-card, and I want to take advantage of the wireless network here.
I think i´ve connected to the wireless-network, but again, I can´t go online.
I lauch Connection Properties, and there is the connection "eth0" activated. But the status switches from Idle to Receiving all the time. The signal strength is almost 100%.

In the properties for "eth0", i´ve wrote the ESSID and the WEP-key for the wireless network. In the Connection Settings i´ve choosed Static IP address, the IP address and Subnet mask is ok, and the Gateway address is clear.

When i write ifconfig in the Terminal, I get this result:
> ifconfig 
eth0 
Link encap:Ethernet HWaddr 00:04:23:65:AB:D4 
inet addr:192.168.2.101 Bcast:192.168.2.255 Mask:255.255.255.0 
inet6 addr: fe80::204:23ff:fe65:abd4/64 Scope:Link 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:1 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) 
Interrupt:5 Base address:0x8000 Memory:fcfff000-fcffffff 

lo 
Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:164 errors:0 dropped:0 overruns:0 frame:0 
TX packets:164 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:13450 (13.1 KiB) TX bytes:13450 (13.1 KiB) 

Can someone help me? PLEASE!!

(i´m sorry for the bad english, but i´m norwegian :-P)

---

### Post by Kuntabunt on 2005-09-13
What do you mean with the gateway is clear?
If you want to connect to the Internet you will need a gateway!

Have you Tried to ping the gateway?

If you reach the gateway it could be a problem with the DNS.
Have you entered a DNS?

Have you tried to ping to a Internet IP-Address like 194.25.134.146 ([www.t-online.de](www.t-online.de))
If that woks you can try to ping the server by its name. If that fials there could be a error with the DNS.

---

### Post by sir_mud on 2005-09-13
is that a centrino notebook or is it a pcmia wifi card (if so what brand)

---

### Post by andrenos on 2005-09-13
It´s a Centrino Notebook.

I tried to ping 194.25.134.146, and then it says "connect: Network is unreachable".
The DNS-address I worte the same address that the Wireless Router has (192.168.2.1). Isn´t this right?

---

### Post by Kuntabunt on 2005-09-14
Ok if it says the network ist unreachable you have no gateway entered.
The gateway address is the IP Address of your router. (192.168.2.1)

---

### Post by andrenos on 2005-09-14
Ok, now I´ve entered 192.168.2.1 in Gateway address, but still it doesn´t work.

I have the address 192.168.2.1 in DNS, is this wrong?
[Here](http://www.andrenos.com/Screenshot.png) is a screenshot of the Interface Settings.. Something wrong?

---

### Post by Miguel on 2005-09-14
First, make sure that the emmiter is not using DHCP.

This is just a wild shot, but on my Dell Inspiron 8600 the WiFi card is eth1, not eth0. If it is your case, try configuring the wireless card at eth1 and then doing 

$ sudo ifup eth1

Also, if you are using the 686 kernel, you might want to install the propietary modules (I'm quite sure that ipw2100 is not a free module). To do this (only if you are using the 686 kernel!!!) try

$ sudo apt-get install linux-686

By the way, yo do need the DNS if you are not using DHCP, if I recall correctly. Of course, if this all looks chinese, blame me and then ask again. I'll do my best.

PS: your settings should be, more or less
IP=192.168.2.x   (x different from 1?)
Mask=255.255.0.0  or  255.255.255.0
Gateway=192.168.2.1
DNS=192.168.?.?

---

### Post by leezer3 on 2005-09-14
Yes, IPW2100 is a free module!
It is proprietary, but the source etc. is available from [http://ipw2100.sourceforge.net](http://ipw2100.sourceforge.net) 
It sounds to me as if you are using an older driver (Ubuntu supplied?)- These were buggy with WPA, but the current version seems to be OK on my IPW2100.

Cheers

-Leezer-

---

### Post by Kuntabunt on 2005-09-14
Miguel is right!

Your configuration is still wrong!

Your IP Address must differ from the Gateway Address!

And the Gateway Address have to be the IP Address of your router!
The router often is configurable with the IP Address so find out the right Address of your router!
As IP Address you have to take a free IP Address in the same Network as the router!


Example:

The IP Address of the router is 192.168.2.1 and SubNetMask 255.255.255.0
and a no other PC in the Network uses the Address 192.168.2.12

In this configuration is the Netork 192.168.2.0 this mens that all IP Addresses in the range 192.168.2.1 to 192.168.2.255 are in the same Network and can communicate directly without an router. Your PC can only communicate within the network. If you would like to communicate with an other IP Address may be in the Internet your PC have to take the Gateway, this is the router. The router gets the message from your PC and send it to a otner netork may be the Internet.

If your router have the IP Address 192.168.2.1 and SubNetMask 255.255.255.0, this is realy important!!! And a no other PC in the Network uses the Address 192.168.2.12
The most routers have an integratet Name Server so the Name Server Address should be the same as the router address.

Than try the configuration:
IP-Address:      192.168.2.12
SubNetMask:   255.255.255.0
Gateway:         192.168.2.1
Name Server:  192.168.2.1

If the internet is not running try again to ping the router:
ping 192.168.2.1

---

### Post by Miguel on 2005-09-15
leezer, thanks for the info about the ipw2100 module. I use the ubuntu 5.04 module. 

BTW: Source forge states you need firmware. Is this firmware free in the gpl sense?

---

