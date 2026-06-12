---
title: "Updated to intrepid: eth0 gone, wireless works fine"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bencoder on 2008-10-04
I just updated to the beta of intrepid, and my ethernet card seems to have gone. It's running a dell vostro 200 with on board ethernet.

ifconfig:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:173245 (173.2 KB)  TX bytes:173245 (173.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:ee:00:df:87  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:eeff:fe00:df87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9984121 (9.9 MB)  TX bytes:8255015 (8.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-EE-00-DF-87-66-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



As you can see, my wireless works fine, so this isn't a huge problem, but it does seem a bit silly to have to connect via wireless to the router that's right next to me. It worked perfect under 8.04.

Thanks for any help/ideas.

Ben

---

### Post by iponeverything on 2008-10-04
Its old stuff, but it might help you out.

[http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

---

### Post by tonus on 2008-10-04
I have the same problem on a thinkpad x300 after update to intrepid beta1. Just to be sure I tried the intrepid beta1 livecd, problem also occurs there, so it's not update related.

---

### Post by tonus on 2008-10-04
Oops, should have read the Known Issues on [http://www.ubuntu.com/testing/intrepid/beta]("http://www.ubuntu.com/testing/intrepid/beta") more carefully. It's a known problem and going to be fixed later on.

> A problem that could result in corruption of the firmware on Intel GigE ethernet hardware has led to the disabling of the e1000e driver in the Linux kernel included in Ubuntu 8.10 Beta. Ethernet devices that use this driver cannot be used with Ubuntu 8.10 Beta; support for this hardware will be re-enabled in daily builds immediately after Beta and this issue will be resolved for the Ubuntu 8.10 final release. [https://bugs.launchpad.net/bugs/263555]("https://bugs.launchpad.net/bugs/263555")

---

### Post by Kuroyume on 2008-10-04
your hardware is most likely affected by this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555)

So in order to keep your ethernet from frying the driver is disabled. A fix has been issued, and will probably make it's way to the repositories soon. DO NOT try to activate your ethernet until you get the fix, or you may kill your network card.

---

### Post by bencoder on 2008-10-04
Ah, thank you, I did notice that but I'm pretty sure my card is not a GigE card. But on the forum message posted above it mentions that some 100mbit cards are not supported by the e100 driver, so I guess I fall under that category.

Thanks again, I'll survive on wireless for now :)

Ben

---

