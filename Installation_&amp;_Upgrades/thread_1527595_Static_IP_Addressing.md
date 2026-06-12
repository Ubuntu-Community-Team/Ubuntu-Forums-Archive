---
title: "Static IP Addressing"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by keiffee30 on 2010-07-09
Dear Anybody

I have got a problem with setting the IP Address on my new install of 10.04. 

I have always set the IP and other network setting like this 
 [Network setting]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html")

I have done this in 10.04 and when i rebooted the PC i couldn't get on to the internet nor the local net. I looked in the network setting in 
system - Preff - network connections and i couldn't find the eth0..... **it had gone. **

i opened up nano and made sure that i had typed in all the information into the 
**/etc/network/interfaces**
and in the
**/etc/resolv.conf **
All was OK i took it back to how i found them and then i go a network connection to the internet/local LAN. 

Could someone please tell me what i have done wrong OR is it not poss to change settings using the terminal / sudo in Ubuntu 10.04 any more ??????

---

### Post by &#963;&#954;&#940;&#955;&#945;86 on 2010-07-09
I would like know this as well.

---

### Post by Devi1903 on 2010-07-09
Please post your working and not working interfaces files

---

### Post by karmic-koala on 2010-07-09
So just to clarify you are able to connect once you issue the eth0 up command?

---

### Post by efflandt on 2010-07-10
I am just guessing that network manager has certain things locked, because I know that alternative gui wireless setting programs and things are incompatible with network manager.  So maybe you should uninstall network-manager if you want to set things manually from terminal or console.  Of course you need to use sudo to edit system settings, but if you didn't, you would realize that when you tried to save files.

What you linked to does say "Ubuntu ships with a number of graphical utilities to configure your  		network devices.  This document is geared toward server administrators   		and will focus on managing your	network on the command line." so manual settings may compete with those gui programs.

---

### Post by lisati on 2010-07-10
As an aside: I prefer to let my router(s) handle setting static IPs, it can help avoid addressing conflicts if I decide to hook one of my machines up to a different network, or reconfigure my own network in some fashion - I have two routers. It can also help reduce the amount of tinkering with configuration files as well.

---

### Post by Morbius1 on 2010-07-10
> **lisati said:**
> As an aside: I prefer to let my router(s) handle setting static IPs, it can help avoid addressing conflicts if I decide to hook one of my machines up to a different network, or reconfigure my own network in some fashion - I have two routers. It can also help reduce the amount of tinkering with configuration files as well.
I can't recommend this suggestion enough. The router basically has a lookup table converting the MAC address of the network card to a specific ip address. One other advantage not mentioned by lisati is that since it's looking at the physical address of the network card it's independent of the Operating System. Change OS's and the ip address will not change.

It's worth looking at the documentation of your router to see if it has this capability. It goes by different names:
"DHCP Address Reservation", "Static DHCP", "reserved DHCP", "Reserved leases", and "Pre-assigned DHCP" .

---

### Post by keiffee30 on 2010-07-17
Morbius1 i have had a look at the router and found what you are saying about DHCP Address Reservation list. So i take it that if i was to set the my MAC and the DHCP address in the reservation list then i would keep the IP address for every. Just like a static address? 

Would this also work with Print servers, and any other nodes that i might have ?

The only reason i had static addressing is to RDC into the PCs on site and also keep a tag on what is going on when the router emails me the sys log. this would also help when i VPN into my PC.

I think this would be a way forward for me. Many thanks for all you help in this matter.

---

### Post by Morbius1 on 2010-07-17
Anything that has a mac address should work. I've set static ip addresses on a MacBook, an iPod, and an iPad. Just remember that you need to keep all the machines set to their default of getting their ip address from the router.

---

