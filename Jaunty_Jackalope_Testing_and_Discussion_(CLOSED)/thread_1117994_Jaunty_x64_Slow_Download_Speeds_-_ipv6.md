---
title: "Jaunty x64 Slow Download Speeds - ipv6?"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dream_coder on 2009-04-06
Hello, I have installed Jaunty x64 on both my laptop and PC switching from Intrepid (Clean Install), the problem is when I used Usenet on Intrepid and also windows I always maxed out my connection at a speed of 2500 or just below (I am on 20mb) but now with Jaunty I am only getting a maximum of 1000, also for some reason when I am downloading on the main PC the laptop is extremely slow when browsing etc.

The PC is connected to a router (TPLink TL-WR541G) via a cat6 cable and the laptop is connected via wireless, I never had this problem with Intrepid or Windows so I was thinking maybe it is ipv6? I am not sure but my speed and bandwidth allocation is definitely effected.

I have tried two different Usenet Clients and they both do the same thing (SABNZBD & Alt.binz).

Maybe someone can shed some light on this? or had the same problems?

thanks.

My ifconfig from my laptop: 

> eth0      Link encap:Ethernet  HWaddr 00:a0:d1:a5:df:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:246 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:832 (832.0 B)  TX bytes:832 (832.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:c0:03:6f  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:13600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5737123 (5.7 MB)  TX bytes:2345886 (2.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-C0-03-6F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


EDIT :

I noticed that the MTU settings on my pc were set at 576 I changed this with the command ifconfig eth0 mtu 1500 and speeds have tripled, so I manually entered my information into the network manager and set the MTU to 1500 (Maximum size for Ethernet I believe) rebooted and it seems to have speeded up my downloads to 1500.

If there are any other tweaks I can do to this connection please let me know.

EDIT:

Now with a mtu of 1500 I am downloading at 1500 and with Intrepid and Windows both vista and XP I get a download speed of 2500 so how can I further what I have done? any info appreciated!

---

