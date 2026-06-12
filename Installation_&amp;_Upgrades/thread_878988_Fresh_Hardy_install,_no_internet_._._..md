---
title: "Fresh Hardy install, no internet . . ."
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by madhartigan on 2008-08-03
This is already in one of my other posts, [HERE](http://ubuntuforums.org/showthread.php?t=877967) but I think it should actually be a separate thread since it is a separate topic.  (Also, I'm unable to delete the message in the other thread)



I just completed a fresh install of Ubuntu 8.04 LTS Desktop. 

I'm unable to connect to the internet. I have a Marvell Yukon Gigabit Ethernet port on my motherboard and Ubuntu is able to see the adapter but, I'm unable to connect to the internet.

The internet is accessed via DSL and I'm having no problems with it on this Windows machine so I know I have connectivity. I'm not even able to connect to my router at 192.168.11.1 (It's a Buffalo router). The DHCP lease sees my machine, but the MAC Address is weird.

When I go to System>Administration>Network Tools, the Devices tab displays:

Network Device: Loopback Interface
Protocol:IPv4
IP Address: 127.0.0.1
Netmask: 255.0.0.0
Broadcast: n/a
Scope: n/a

Protocol: IPv6
IP Address: ::1
Netmask: 128
Broadcast: n/a
Scope: Host



When I change the Network Device to eth0 it displays
Protocol: IPv6
IP Address: fe80::201:XXXX:XXXX:9cc0
Netmask / Prefix: 64
Scope: Link

I also have the option to select eth0:avahi. That displays:

Protocol: IPv4
IP Address: 169.254.x.x
Netmask/Prefix: 255.255.0.0
Broadcast: 169.254.255.255



I'm unable to configure the Loopback Interface device and when I try to configure the eth0 or eth0:avahi, I get an error saying the interface does not exist.

I'm looking for solutions but, if anyone can provide suggestions, I'm willing to listen.

---

### Post by hal8000 on 2008-08-03
Make your your adapter is seen by ubuntu:

dmesg | grep eth

should return information about all your ethernet cards.
The yukon chipset uses module skge  (formerly sk98lin) so a quick 
lsmod should display your loaded modules.

You can then manually configure your network with static addresses even if you are using DHCP, assinging the card a high address will avoid a possible
conflict:


sudo ifconfig  eth0 192.168.11.221 netmask 255.255.255.0

run ifconfig to check that its taken:
ifconfig eth0

Now add a route to your gateway (router)

sudo route add default gateway 192.168.11.1

you should now be able to ping your router:
ping 192.168.11.1

finally if your router has your ISP's DNS servers, set /etc/resolv.conf to point to your router (alternatively set the nameserver to your ISP's nameserver)

Edit /etc/resolv.conf

nameserver 192.168.11.1

If static addressing works then use ubuntu to setup your ethernet card. You may also find this link useful:

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

---

### Post by madhartigan on 2008-08-03
I guess I'm going to have to take this step by step.

My DSL modem connects to my router in "Bridge" mode.
My router handles the DSL connection through PPPoE protocol.  I don't think my ISPs nameservers are involved with anything I'm using but, i could be wrong.

When I type in dmesg |grep eth, here's what I get:

```

[   46.040566] skge eth0: addr 00:01:29:d4:9c:c0
[   47.980182] Driver 'sd' needs updating - please use bus_type methods
[   55.730831] Driver 'sr' needs updating - please use bus_type methods
[   63.584842] skge eth0: enabling interface
[   66.665547] skge eth0: Link is up at 100Mbps, full duplex, flow control both
[  126.380556] eth0: no IPv6 routers present
[  452.132291] NETDEV WATCHDOG: eth0: transmit timed out
[ 3735.395539] NETDEV WATCHDOG: eth0: transmit timed out
[ 6958.690766] NETDEV WATCHDOG: eth0: transmit timed out
[ 9522.334767] NETDEV WATCHDOG: eth0: transmit timed out

```


I tried all of the other steps you mentioned and when I ping I don't get any response.

I'm at a loss.

now when I ping, I'm getting:

ping: sendmsg: No buffer space available

I don't know what's going on but, it's definitely frustrating.  In the past, when I load a fresh ubuntu, there are no problems with the internet.  It's right there, up and running.  I don't understand what's up with this version.

---

### Post by tonychar on 2008-08-03
I was having no internet access after a fresh install of Hardy Heron, (overwriting Windows) but I did not have the ethernet cable attached (and modem on) when I did the instal.  (laptop)  I think the install couldn't configure my ethernet and internet connections, because there was no connection.

Manual attempts to configure the settings failed, so I re-booted, and re-installed Hardy Heron with the ethernet cable in place and working. 

Clicked on the Firefox icon and connected immediately.  I hope this is your problem too.

---

### Post by Pumalite on 2008-08-03
The best is to have a router to provide you with DHCP and a dynamic ip at boot during installation.

---

### Post by madhartigan on 2008-08-03
> **Pumalite said:**
> The best is to have a router to provide you with DHCP and a dynamic ip at boot during installation.

That's the thing, I DO have a router that runs DHCP and is "willing" to provide an IP to whatever is connected to it.


I'm going to try to reinstall, despite the fact that my ethernet cable was connected during the last install and the port's connectivity LED was definitely lit.

Perhaps that will help.

---

