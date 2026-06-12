---
title: "[SOLVED] Upgrade Failed (Network Manager)"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2008-10-03
I have just upgraded my Toshiba Laptop to Intrepid. Halfway through the upgrade process I saw messages that network manager was in problems due to a missing resource, although the resource was not mentioned. 

Having finished the upgrade I have a working laptop except for wireless. It appears that my wireless card is enabled and is capable of working but I have no network manager applet.

ifconfig indicates that the wireless is active but unassigned.

Any clues as how to proceed.

---

### Post by Peter09 on 2008-10-03
ifconfig

> eth0      Link encap:Ethernet  HWaddr 00:0e:7b:73:30:9e  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169879 (169.8 KB)  TX bytes:24289 (24.2 KB)

eth1      Link encap:Ethernet  HWaddr 00:13:ce:e5:59:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:63 errors:0 dropped:12 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xc000 Memory:cffff000-cfffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13094 (13.0 KB)  TX bytes:13094 (13.0 KB)



and 
lshw -C network

>   *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:e5:59:ba
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:0e:7b:73:30:9e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.0.12 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes


---

### Post by hansdown on 2008-10-03
Hi Peter09.

Sef has a tread that may help.

[http://ubuntuforums.org/showthread.php?t=936696](http://ubuntuforums.org/showthread.php?t=936696)

Go to the bootom of the post for wireless help.

---

### Post by iponeverything on 2008-10-03
do:

nm-applet&

after that first manual start, it will start showing up again..

---

### Post by Peter09 on 2008-10-03
Hi Hansdown, sorry cannot find the section you have mentioned in this thread.

Hi iponeverything issuing sudo nm-applet seems to have done the trick.

---

### Post by JacquiOh on 2008-10-03
Hi Peter09,

I have almost the same problem

[here]("http://ubuntuforums.org/showthread.php?t=936924")

The difference seems to be that your wireless has the "logical name" of eth1 and mine has no logical name at all!... end result the same however.

I had the network manager error about 3 times during my install, also about the rescource not available, but never mentionning which resource. I tried reinstalling network manager through synaptic but nothing either.

I found several matching bug reports but not much I understand.

---

### Post by Peter09 on 2008-10-03
Yes, I did re-install network manager as well, but is was not until I ran the applet that things worked. However I think I have always had a viable wireless card. Have you have seen the thread about the intel driver bricking hardware, I think they have blacklisted that driver. So if you have a machine that needs that driver you will not get an internet connection.  However I think thst is for a wired connection.

---

### Post by Peter09 on 2008-10-04
By running nw-applet I can now get a wireless connection, but how do I make it stick to come up every time.

---

