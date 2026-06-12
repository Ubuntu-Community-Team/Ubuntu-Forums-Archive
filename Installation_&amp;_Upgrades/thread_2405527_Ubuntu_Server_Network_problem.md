---
title: "Ubuntu Server Network problem"
date: 2018-11-07
forum: Installation &amp; Upgrades
---

### Post by jordygames on 2018-11-07
Dear,

I'm trying to make a server of my old pc with Ubuntu Server. I downloaded the iso file to a stick and booted my old pc. 
When I had to choose my network, the machine says: "DHCPv4 had supplies no adresses", so it is not going automatic. Then I choose for manually, but I don't really know what I had to fill in subnet, gateway, adress and name servers. Someone who can help me?

Thanks in advance!
Jordy

---

### Post by wyliecoyoteuk on 2018-11-07
Depends on your network.
for example, assuming yours is a home network with IP addresses in the 192.168.1.xxx range:
network is 192.168.1.0, your router is 192.168.1.1, your subnet mask is 255.255.255.0, and you want the PC to be on 192.168.1.101 (so that it is outside the DHCPv4 scope of your router):
address:192.168.1.101
subnet: 192.168.1.0\24
gateway: 192.168.1.1
Name servers: 192.168.1.1,8.8.8.8

---

### Post by jordygames on 2018-11-07
Thank you for your answer! 
Unfortunately, it still gives "network configuration timed out, please verify your settings". 
Do I have to install Linux first on my old pc (Windows 7 now)
Or do you know what it could be?

Thanks in advance!

---

### Post by wyliecoyoteuk on 2018-11-07
Make and model of PC might help.
It might be that the network card is not supported, or needs firmware (very likely if it is wireless).

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

> Then I choose for manually, but I don't really know what I had to fill  in subnet, gateway, adress and name servers. Someone who can help me?

If you have filled the 'sample' data provided by [**[COLOR=#000000]wyliecoyoteuk[/COLOR]**]("https://ubuntuforums.org/member.php?u=553677"), it did not worked because your 'network' is different. You can try manually once again, but before it need to do some homework. If you have any other PC or a smart phone connected to same router, go to network settings/information and note down the IP address, subnet/netmask and gateway (address) from it. there are three possibilities..

IP Add 192.168.xxx.xxx Netmask/subnet 192.168.xxx.0/24 or 255.255.255.0 and gateway 192.168.xxx.254 or 192.168.1.1
IP Add 172.16.(0-32).xxx Netmask/subnet 172.16.(0-32).0/16 or 255.240.0.0 and gateway 172.16.(0-32).254 or 172.16.(0-32).1
IP Add 10.xxx.xxx.xxx Netmask/subnet 10.xxx.xxx.xxx/8 or 255.0.0.0 and gateway 10.xxx.xxx.1

When you find anything similar just change the x only in yyy.yyy.yyy.xxx from the obtained settings, rest you will fill as it is. 

Additional link to obtain [Network Details from Android device]("https://kb.k12usa.com/Knowledgebase/Find-the-IP-address-of-an-iPad-or-Android-Tablet") (Only when connected to Wifi router). Even if after obtaining the details there is confusion, please post obtained IP Adress and Netmask. Will try to help. 

P.S.- If the obtained IP Adress is not from the range/s mentioned above, please do not post it.

Regards,
Mitesh

---

### Post by wyliecoyoteuk on 2018-11-10
Sorry, I should have been clearer in stating that it was an example, to be adjusted to match his own network.
Thank you Mitesh

---

### Post by mitesh.agrwl on 2018-11-10
> **wyliecoyoteuk said:**
> Sorry, I should have been clearer in stating that it was an example, to be adjusted to match his own network.
Thank you Mitesh

No need to be, you were pretty clear that it was example. Its sometimes we skip the part in eagerness to find the solution. :cool::)

Regards,
Mitesh

---

