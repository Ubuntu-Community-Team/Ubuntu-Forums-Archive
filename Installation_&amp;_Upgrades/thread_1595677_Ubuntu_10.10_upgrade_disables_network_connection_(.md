---
title: "Ubuntu 10.10 upgrade disables network connection (with fix)"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by GMottram on 2010-10-13
I just upgraded to Ubuntu 10.10 desktop using the update manager. After completing the installation and rebooting, my Ethernet connection would not work at all. It was using DCHP and I tried manually setting the IP address and route to my router, etc. but even ping would not function.

My solution was to disable IPV6 as per the directions on the Ubuntu site. Unless you are on an IPV6 network, I don't think there is any benefit to having this protocol enabled. I don't know if IPV6 was enable on my computer in the past (I didn't pay much attention because the network connections worked fine) or if perhaps there is a new conflict between INET and IPV6.

To check if IPV6 is enabled, type:

     lsmod | grep ipv6

If it comes back with a module name, IPV6 is enabled.

The following commands require root access (su or sudo)...

To disable IPV6, edit the following file (it did not already exist in my case):

    /etc/modprobe.d/blacklist.local

And add the following line:

    blacklist ipv6

Save the file and reboot. You can recheck if IPV6 is installed, as per above but your network connection should be working again. It worked for me but your mileage may vary.

---

### Post by GMottram on 2010-10-14
Well, I was wrong. That wasn't the problem. My connection was down again this morning even after multiple reboots.

Right now the only thing that does work is booting an older kernel and not using the kernel that comes with Ubuntu 10.10. There must be a problem with the Ethernet drivers. In my case the system log tells me I have:

PCI Express: 2.5GB/s
Intel (R) Pro/1000 Network Connection

The symptoms include an unreachable network. I can't even ping my router. Ping tells me: no route to host.

---

### Post by cpc1114 on 2010-10-18
Hey this happened to me too, you should clear CMOS on your motherboard and your network should work again. This worked for me, give it a try.

Chris

---

### Post by Ray! on 2010-10-23
Thanks.  After resetting the motherboard the network connection returned to normal!  Many Thanks!!

---

### Post by renaat on 2010-11-01
Similar problem here, after an upgrade from Ubuntu 10.04 to Ubuntu 10.10 (64-bits version), the wired network no longer worked. Network driver: also e1000e. 

There's another workaround: use an old kernel. The kernel 2.6.32-25 (still installed after an upgrade) works.

---

