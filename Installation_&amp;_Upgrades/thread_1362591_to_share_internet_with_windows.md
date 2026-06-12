---
title: "to share internet with windows"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by mahdiar on 2009-12-23
hi 
my computer is connected to the Internet through a router . I want to share my Internet with two computers using windows . please help me .

---

### Post by gordintoronto on 2009-12-23
Connect each of the computers to the router, and you can share the Internet.  That's what a router does.

---

### Post by mahdiar on 2009-12-24
i know that . i want to know how to share my internet connection .
thanks

---

### Post by HomoGleek on 2009-12-24
> **mahdiar said:**
> hi 
my computer is connected to the Internet through a router . I want to share my Internet with two computers using windows . please help me .
Windows .... Internet .... Shudder! (jj)

Are you using Ethernet cables or WiFi? How many outputs does your router have?

---

### Post by mahdiar on 2009-12-24
i'm using Ethernet cables and my router has  4 outputs .

---

### Post by adam814 on 2009-12-24
I've done this in 9.10 server.  You'll need at least 2 NICs to make it work: one facing the internet (connected to your router) and one for your local subnet (must use static IP on this address).  Run the one from your subnet to a switch or hub that you'll connect your Windows machines to.

You need to set up a few things on your machine:
1) dnsmasq - lightweight caching DNS server for your local subnet that pretty much works out of the box
2) dhcp3-server - ISC DHCP server to assign IP addresses on your local subnet (yes dnsmasq also does DHCP, but I found configuring it frustrating)
3) enable kernel forwarding - edit /etc/sysctl.conf and uncomment the relevant lines to enable IPV4 and/or IPV6 forwarding per your needs
4) IP Masquerading (NAT) - see [http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm)

There are decent guides out there for getting all of those set up.  I hope this helps point you in the right direction here.  Good luck.

Notes:
I had no luck getting ufw to work with the listed iptables rules as "legacy" rules so I removed ufw and only use iptables.  Your results may vary.
I had no particular need to do this, I just wanted to understand how a router works.
I used 9.10 Server Edition, but there's no reason it wouldn't work with the Desktop version too, I just didn't want the extra overhead of an X server on a headless router.
You might be able to do it using a DHCP relay agent such as dhcp-helper instead and not run DNS or DHCP on your machine, just forwarding and the IP Masquerading portion, but then your machine is more of a switch than a router and that doesn't sound like what you want.

---

### Post by mahdiar on 2009-12-25
Thank you very much but i have only one NIC . when i had windows xp i could do that . i changed my local area connection ip and change the others ip too . i didn't have any problem .

---

### Post by antmenj on 2009-12-25
Plug your internet into the WAN port on your router.  Set router to serve DHCP.  You may need to clone MAC address.
Plug you ubuntu computer into one LAN port and up to 3 other computers into the others LAN ports.  You should have internet on all 4 computers.

---

### Post by antmenj on 2009-12-25
Oh hang on.... Do you have dialup internet?  If not what sort?

---

### Post by mahdiar on 2009-12-25
no it's dsl . In fact it's connected to a hub and it has 4 LAN port .

---

### Post by louieb on 2009-12-25
> **mahdiar said:**
> hi 
my computer is connected to the Internet through a **router **. 

> **mahdiar said:**
> no it's dsl . In fact it's connected to a **hub **and it has 4 LAN port .

A router will work as described in earlier posts for internet sharing. 
dsl modem -> router -> other computers. 

Never have had to set up a hub - but the setup would be completely different from setting up a router.

dsl modem -> computer -> hub ->  other computers.

---

### Post by antmenj on 2009-12-26
Did you get it to work?

If not what is the model of the dsl modem and the hub/router?

---

### Post by adam814 on 2009-12-26
So if you only have one NIC how did you share internet with all Windows machines?  I'm guessing it was a USB connection to the DSL modem and an ethernet cable to the "in" or "wan" port on the hub.

You still need that (hopefully your dsl modem is recognized by Linux).  Just make sure kernel forwarding is on and you're running a DHCP server to listen on your ethernet interface (probably eth0).  I use dhcp3-server and the config file (/etc/dhcp3/dhcpd.conf) has a lot of example configurations you can work from.  You'll need to make sure the "option domain-name-servers <server>" is set to your internet-facing IP address so LAN-side computers have DNS service.

I just run a DNS server as well since it speeds things up using a cache.

Also I'd recommend checking your firewall rules to make sure they're up to par for what you have in mind.  Otherwise you're basically connecting your poor Windows machines directly to the internet.

---

### Post by mahdiar on 2009-12-27
first excuse me because i know a little about IT:)
let me explain more . this is my network 
[IMG]http://www.freeimagehosting.net/uploads/10ca683311.png[/IMG]

---

### Post by adam814 on 2009-12-27
Sorry if I came off condescending, that wasn't my intent.  I just couldn't get my head wrapped around your particular setup.  Looking at the picture I don't have a clue what you're trying to do exactly.  If all your computers are connected through the dsl router like in the picture why did you need Windows Internet Connection Sharing?

---

### Post by mahdiar on 2009-12-28
two or three connections cannot connect simultaneously so one of us must share his connection to the others . i want to know how can i share my connection or how to use a shared connection .
thanks a lot for your helps

---

### Post by mlho on 2009-12-28
Like others, I am baffled what you are trying to do.

The router, if correctly set-up, should serve an internet connection to all 3 computers.

---

### Post by antmenj on 2009-12-28
So your using the adsl modem/router but not the adsl part and the internet is from the wireless modem is that right?

Tell us the models of the wireless modem and the billion router.

---

### Post by Mark Phelps on 2009-12-28
Your diagram makes no sense ...

Computers have to connect via a cable to SOMETHING. Your diagram shows the cables connecting to each other.  That is simply not possible.  At the very least, the cables would connect via a passive Hub.

In your diagram, the computers could connect via networking cables to the router. But if this is a wired router, it can not connect to the wireless modem unless there is a network port on the modem.  Even then, HOW it would connect depends on the nature of that port.

The wireless modem COULD connect to only one of the PCs, but then, the computers could not connect BOTH to the router and to the PC.

---

### Post by aikiwolfie on 2009-12-29
This has me totally baffled as well.

**What type of modem do you have? Maker and model please.**

Do you have an ADSL router or a hub? The distinction is important. A router is different from a simple hub. If you have a router connected to your modem then there should be no issues with multiple connections. If on the other hand you're using a hub then you'll need to set up on of the PCs to act as a router. Normally when you do this you'll have two Ethernet ports on the PC. One will connect to the hub, the other to the modem. I've never seen it being done with the modem connected to the hub directly.

**Again we need to know the Maker and model of your router or hub.**

Which PC will be in control of your network? If it's Ubuntu, which version are you using? This might effect the setup.

I can't remember exactly how internet connection sharing works in XP. But I think the two PCs end up sharing an IP address. On this network all your PCs will need a different IP address. For a small network like this DHCP is normally the best way to go.

---

### Post by aikiwolfie on 2009-12-29
I just found this tutorial for sharing an internet connection. It may be of use.

[http://digg.com/d31DE5K](http://digg.com/d31DE5K)

---

### Post by mahdiar on 2009-12-30
> **antmenj said:**
> So your using the adsl modem/router but not the adsl part and the internet is from the wireless modem is that right?

Tell us the models of the wireless modem and the billion router.

yeah your right

its
      " billion wireless router BiPAC 7300G "

---

### Post by mahdiar on 2009-12-30
> **aikiwolfie said:**
> I just found this tutorial for sharing an internet connection. It may be of use.

[http://digg.com/d31DE5K](http://digg.com/d31DE5K)

excuse me but digg.com is filtered in my country

---

### Post by adam814 on 2009-12-30
Here's the actual article the digg.com page links to:
[http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/](http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/)
Maybe that won't be filtered for you.

---

### Post by mahdiar on 2010-01-01
Thanks a lot . my problem is solved .

---

