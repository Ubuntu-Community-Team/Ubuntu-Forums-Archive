---
title: "No network or USB ports after MB switch"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by kaspar_silas on 2013-05-17
I really hope someone can guide me in the right direction with this as I am pretty damn stuck presently. I have a desktop computer which has just had its motherboard replaced and now ubuntu has decided not to play nice with networking or its USB ports. 

Ubuntu 12.10 was already installed on the hard drive so I connected this drive up and it booted up perfectly. However once booted I realized it is not connecting to the network. I lazily thought I'd solve this by upgrading to 13.04 using a bootable USB (made elsewhere). This booted to some preliminary screen (purple with two white icons at the bottom) but then seemingly jumped to a black screen and went no further.

So it seemed I would have to fix the networking issue to progress. The computer is plugged directly into a home router (the standard BT one). The cable and router are fine as if I plug them into my laptop it works automatically. However once plugged into the desktop even if I just try and ping anywhere it fails:

$ ping [www.google.com](www.google.com)
unknown host

even if I try and ping the router by its actual address this fails:

$ ping 192.168.1.254
unknown host

Local pinging works of course:
$ ping localhost
[Standard Output]

if I try "route" I also get absolutely nothing:
$route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

I thought I would look in the dmesg log on boot up to see if this reveals anything. It reveals a very worrying tale:

[ 77.860885 ]  ---- [ cut here ] -----
[ 77.860899 ]  Warning: at /build/buildd/linux-3.5.0/net/sched/sch_generic.c:255 dev.watchdog+0x24a/0x260()
[ 77.860902 ]  Hardware name: To be filed in by O.E.M.
[ 77.860905 ]  NETDEV WATCHDOG: eth1 (r8169): transit queue 0 timed out
[ 77.860908 ] Modules linked in: ***about 10 lines of modules***
[ 77.8610041 ]  Pid: 0, comm: swapper/3 Tainted: P.    0 3.5.0-22-generic # 34-Ubuntu
*** then a massive call trace ***

I then thought I might be able to connect by using a wifi dongle to update ubuntu.
However plugging this whilst watching dmesg reveals a host of
"usb 1-2: device descriptor read/64, error -32"
errors. Then a
"usb 1-2: device not accepting address 9, error -32"
A few more read/64 errors and finally a 
"hub 4-0:1.0: unable to enumerate USB device on port two."

So now I am totally out of ideas?  Can anyone think of anything or even suggest the most likely error to start on.

p.s. I am going to be away for a few hours so I'll be slow to respond but any help is greatly appreciated

---

### Post by kaspar_silas on 2013-05-18
Just a quick update. The solution to this mystery (found via this thread [http://ubuntuforums.org/showthread.php?t=2114055](http://ubuntuforums.org/showthread.php?t=2114055) ) is merely to go into the MB bios settings and enable IOMMU.

---

