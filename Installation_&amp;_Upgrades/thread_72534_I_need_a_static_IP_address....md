---
title: "I need a static IP address..."
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by XtremeGamer99 on 2005-10-06
Okay, I'm not sure what's wrong. I need static IP address 192.168.1.160 to work with my Apache server. However, when I go to System > Admin > Networking and change my ethernet connection (eth0) to static ip, and input:

```
IP Address: 192.168.1.160
Subnet Mask: 255.255.255.0
Default Gateway: 65.14.252.33
```

Now, I have a LinkSys Wireless Router Model WRT54G (I'm hooked up by cable, though). I'm not sure what I need to post to get this fixed, so I might as well give all the information I can in this post.

This is basically what I have configured to it:
```
Local IP Address: 192.168.1.1
Subnet Mask: 255.255.255.0

-------------------------

DHCP Server: Enabled
Starting IP  Address: 192.168.1.100
Maximum Number of  DHCP Users: 50
Client Lease Time: 0 minutes (0 means one day) 	  	 
Static DNS 1: 0.0.0.0
Static DNS 2: 0.0.0.0
Static DNS 3: 0.0.0.0
WINS: 0.0.0.0
```

From the status page:
```
Subnet Mask: 255.255.255.255
Default Gateway: 65.14.252.33 	  	
DNS 1: 205.152.144.23 	  	 
DNS 2: 205.152.132.23 	  	 
DNS 3:
MTU: 1492
```

From the Application & Gaming (Port fowarding):
```
Application > Start > End > Protocol > IP Address > Enabled?

HTTP > 80 > 80 > TCP > 192.168.1.160 > Enable
```

I've also looked at the DDNS options - the one that is supposed to update dyndns.org to my public IP address - It updates successfully.

Everything should be running okay, but I don't know what's wrong. Apache is running - I can access localhost. Can someone help me out?

---

### Post by Zelut on 2005-10-06
why do you need a static IP on your localhost?  I'm assuming you've got a site built with apache & you're trying to access that from the outside?  You use dynDNS to update your WAN IP with the dyndns site you made (ie; xxx.homeip.net)?  All you should need to do is use port forwarding to that machine on the router.

I think if you were more specific with what you needed to do we could help you out some more.

---

### Post by XtremeGamer99 on 2005-10-06
I want people from outside my network to access my site, yes. It updates the DynDNS database fine - I've already checked. And I already said that I have my router enabled to forward port 80 to 192.168.160, however, in order to do that, I need a static IP address. Right now, my System > Admin > Networking is set to Static IP, and I've inserted these variables:
```
IP Address: 192.168.1.160
Subnet Mask: 255.255.255.0
Default Gateway: 65.14.252.33
```
Which should give my computer a static IP address. However, when I do that, and try to access xgamer.ath.cx (my host), it can't find any contact. I know it's not the DynDNS updater - That's working. I know it not the port forwarding - My Apache is listening on port 80 and it is enabled. So it must be that I don't have a static IP address. This all worked when I had Windows XP Pro. It was the same router options, almost the same Apache configuration, etc.

I don't know how I can be more specific than that...

---

### Post by Zelut on 2005-10-06
Well, the way I do it for my site (using the same idea as you) is set port forwarding to my box from the router but don't set a static IP.  I use my router to assign the IP to that box (via MAC address).  Even though my router acts as a DHCP server if it sees the MAC address it'll give it that specific IP each time, make sense?  See if yours will allow that.  If not you may have a problem with your router acting as a DHCP server and your computer trying to use its own IP...

---

### Post by XtremeGamer99 on 2005-10-06
Well, i don't know what a MAC Address is, but I did find something about it on my routers config page:

[http://xgamer.insder.com/bleh/Screenshot.png](http://xgamer.insder.com/bleh/Screenshot.png)

What do I need to do in order to fix this whole mess?

---

### Post by XtremeGamer99 on 2005-10-06
Also, I don't know what my MAC address is...

---

### Post by Zelut on 2005-10-06
well using ifconfig or even the network manager will tell you your mac (its generally something like: 00:4f:37:c8:92...)

Uhm, what I would suggest is change your box back to DHCP and port-forward to that.  If your box stays on it will maintain the same IP address.  If you notice that you can't get access check that the IP is the same and update if neccesary.  

Give it a try and let me know if that works

---

### Post by mit on 2005-10-06
HI,

It might be an option with your ISP to be assigned a Static IP.

---

### Post by XtremeGamer99 on 2005-10-06
Okay, well I put in the MAC address into the input feilds that you can see here:
[http://xgamer.insder.com/bleh/Screenshot.png](http://xgamer.insder.com/bleh/Screenshot.png)

I enabled it, saved the settings, returned Ubuntu to DHCP, but nothing is happening. On my Prot Forwarding page, what should I put as my IP? Since I'm on DHCP, I'm not guarenteed the same IP address to use. 

I still don't fully inderstand the MAC Address thing 

[QUOTE=mit]HI,

It might be an option with your ISP to be assigned a Static IP.[/QUOTE]

And pay an extra $20 dollers per month? Maybe, if I wasn't going to run a small personal blog... <_<

---

### Post by MrCheese on 2005-10-07
change your gateway address to the lan-side of the router (eg. 192.168.1.1) rather than wan-side as yo uappear to have configured it. Your system has no route to the outside world as it is configured.

---

### Post by XtremeGamer99 on 2005-10-08
That did it. Thanks!

---

### Post by spot101 on 2006-10-13
You might want to up-grade your firmware too. Your screenshot shows you have firmware 4.00.7. Recent firmware has a number of security related fixes and one for DynDNS.

Spot;) 

> 
Linksys, A division of Cisco Systems, Inc.

Product:                WRT54G

Classification:         Firmware Release History

Firmware  Date:		04/27/2006

Release Date:           05/25/2006

Last Firmware Version: 4.30.5
__________________________________________________________________________
Firmware 4.30.5
- Resolves UPnP vulnerability reported by SANE

Firmware 4.30.2
- Resolves issue with filter name
- Resolves issue where service name for PPPoE cannot be added
- Resolves issue with detecting UHP modems
- Resolves issue where DynDNS Custom and Static accounts cannot be used
- Resolves issue with WEP passphrase not recognizing spaces

Firmware 4.20.7
- Resolved issue with SecureEasySetup button delay
- Resolved issue with SecureEasySetup overwritting current wireless settings
- Resolved issue with not being able to disable SecureEasySetup button
- Resolved issue with Diag light being constantly lit after upgrading to 4.20.6 on v.1 hardware
- Resolved issue with iDefense security vulnerability
- Resolved issue with L2TP disconnect
- Resolved issue with SecureEastsetup long button push not resetting wireless settings

Firmware 4.20.6
- Resolve issues with setup wizard
- Updated wireless security menu
- Resolve issues with port based QoS

Firmware 4.00.7
- Adds SecureEasySetup push button support
- Resolves large file transfer issues
- Resolves issue with enabling TKIP after enabling WEP
- Updated QoS features
- Resolves issues with multiple Access Restrictions policies
- Resolves issue where multicast breaks when MAC filter status changes

---

