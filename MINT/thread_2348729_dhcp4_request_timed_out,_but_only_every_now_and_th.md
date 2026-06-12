---
title: "dhcp4: request timed out, but only every now and then...."
date: 2017-01-06
forum: MINT
---

### Post by dr.fred on 2017-01-06
Hi all!
New to this forum, so bear with me ;)

First things first. You will be delighted to hear that I managed to convince a relative of mine (a senior), who wanted to replace his old rig, to say bye bye to W****** and choose one of those systems usually used by mature adults.
So far so good. He needed some time to accustom himself with the new system, naturally, but everything worked fine. Everything but... the net.

I've at my hand what looks like a DHCP networking problem. The PC is now installed in the house of my relative. I've set it up at my home in almost the same environment (same router, i.e. same type router, same ISP, same cable modem, same PC obviously). During the setup of the PC, I've never had any probs with the inet connection. However, when finally installed in the house of my relative, i've seen recurring connection issues from the beginning:
Every second or third time after boot there is no connection due to missing IP lease (or so it looks). However, a reboot then helps and it gets the lease and works forever and ever until next restart where it doesnt get the IP again and so on... First I suspected this problem has to do with the direct connection from cable modem to the NIC at my relatives house, since in my home setup, of course, there is a home router in between. So I went back and installed an old router of mine and thought this will solve the issue. 

First it worked as intended. But then suddenly, after a reboot, no IP again! Now the setup is almost identical as it was at my home where there never was a problem. I dont know, it makes it hard to guess the culprit.
I've been browsing the net but found not much. I've searched the syslog for clues, grepped for the if name which is enp7s0.

Here is the piece of log when it works:
```
Jan  3 16:27:10 Kasimir NetworkManager[879]: <info>  [1483457230.6676] dhcp4 (enp7s0): activation: beginning transaction (timeout in 45 seconds)
Jan  3 16:27:10 Kasimir NetworkManager[879]: <info>  [1483457230.6777] dhcp4 (enp7s0): dhclient started with pid 1175
Jan  3 16:27:10 Kasimir dhclient[1175]: DHCPREQUEST of 213.196.176.173 on enp7s0 to 255.255.255.255 port 67 (xid=0x1e75fede)
Jan  3 16:27:10 Kasimir avahi-daemon[848]: Joining mDNS multicast group on interface enp7s0.IPv4 with address 213.196.176.173.
Jan  3 16:27:10 Kasimir avahi-daemon[848]: New relevant interface enp7s0.IPv4 for mDNS.
Jan  3 16:27:10 Kasimir NetworkManager[879]: <info>  [1483457230.7433] dhcp4 (enp7s0): state changed unknown -> bound
Jan  3 16:27:10 Kasimir avahi-daemon[848]: Registering new address record for 213.196.176.173 on enp7s0.IPv4.
Jan  3 16:27:10 Kasimir NetworkManager[879]: <info>  [1483457230.7440] device (enp7s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Jan  3 16:27:10 Kasimir NetworkManager[879]: <info>  [1483457230.7446] device (enp7s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Jan  3 16:27:10 Kasimir NetworkManager[879]: <info>  [1483457230.7448] device (enp7s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Jan  3 16:27:10 Kasimir NetworkManager[879]: <info>  [1483457230.7598] policy: set 'Kabelnetzwerkverbindung 1' (enp7s0) as default for IPv4 routing and DNS
Jan  3 16:27:10 Kasimir NetworkManager[879]: <info>  [1483457230.7975] device (enp7s0): Activation: successful, device activated.


```

and now when things go wrong:
```
Jan  3 20:22:55 Kasimir NetworkManager[873]: <info>  [1483471375.6097] dhcp4 (enp7s0): activation: beginning transaction (timeout in 45 seconds)
Jan  3 20:22:55 Kasimir NetworkManager[873]: <info>  [1483471375.6108] dhcp4 (enp7s0): dhclient started with pid 1508
Jan  3 20:22:55 Kasimir dhclient[1508]: DHCPREQUEST of 192.168.0.100 on enp7s0 to 255.255.255.255 port 67 (xid=0x6e6598f8)
Jan  3 20:22:57 Kasimir avahi-daemon[899]: Joining mDNS multicast group on interface enp7s0.IPv6 with address fe80::fc4d:70c:8902:762a.
Jan  3 20:22:57 Kasimir avahi-daemon[899]: New relevant interface enp7s0.IPv6 for mDNS.
Jan  3 20:22:57 Kasimir avahi-daemon[899]: Registering new address record for fe80::fc4d:70c:8902:762a on enp7s0.*.
Jan  3 20:22:58 Kasimir dhclient[1508]: DHCPREQUEST of 192.168.0.100 on enp7s0 to 255.255.255.255 port 67 (xid=0x6e6598f8)
Jan  3 20:23:04 Kasimir dhclient[1508]: message repeated 2 times: [ DHCPREQUEST of 192.168.0.100 on enp7s0 to 255.255.255.255 port 67 (xid=0x6e6598f8)]
Jan  3 20:23:11 Kasimir dhclient[1508]: DHCPDISCOVER on enp7s0 to 255.255.255.255 port 67 interval 3 (xid=0x71f1143c)
Jan  3 20:23:14 Kasimir dhclient[1508]: DHCPDISCOVER on enp7s0 to 255.255.255.255 port 67 interval 7 (xid=0x71f1143c)
Jan  3 20:23:21 Kasimir dhclient[1508]: DHCPDISCOVER on enp7s0 to 255.255.255.255 port 67 interval 14 (xid=0x71f1143c)
Jan  3 20:23:35 Kasimir dhclient[1508]: DHCPDISCOVER on enp7s0 to 255.255.255.255 port 67 interval 20 (xid=0x71f1143c)
Jan  3 20:23:40 Kasimir NetworkManager[873]: <warn>  [1483471420.5873] dhcp4 (enp7s0): request timed out


``` 

There seems to be a dhcp timeout. So what I did as a quickfix is to give it a fixed IP. This seems to work so far. But still, Id like to see DHCP work.
What I do not understand is why the request is from 192.168.0.100 (the PC) once,  but the other time it is from 213.196.176.173 (which might be the WAN interface).
Also, could it be that ipv6 is somehow interfering? Should I deactivate ipv6? 

Perhaps I will also try another switch-port on the router, maybe another router altogether if that does not help.
Ive also read on the inet that blacklisting ipv6 might help. Also, there is the rc.inetd.conf where I could try to set DHCP [0]="no". 
But I cant imagine how that would help.

I ve not installed any proprietary drivers so far since that was not necessary during the setup.
If anybody could give me a hint or two where to start I would appreciate it much....

The specs are like this:
Linux Mint 18, therefore 16.04, Mobo MSI Gaming M3 with Killer E2400 Gigabit LAN

Thx for help!

---

### Post by ajgreeny on 2017-01-06
*Thread moved to **MINT**.* which is more appropriate for the problem and should be a better fit.

---

