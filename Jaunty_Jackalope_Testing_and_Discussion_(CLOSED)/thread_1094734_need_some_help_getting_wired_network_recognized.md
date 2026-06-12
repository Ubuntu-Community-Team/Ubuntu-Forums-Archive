---
title: "need some help getting wired network recognized"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mattisking on 2009-03-12
On Intrepid I had a static IP set for eth0 on my wired NIC in the latest version (for Intrepid) of network-manager.

When I ran the upgrade path from within Intrepid to Alpha 6 of Jaunty, I did have a few problems around python and a couple other minor issues mostly involving applications installed from other repos... but no real network problems reported. Since I ran into a couple problems, however, the upgrade process didn't reboot and just let me sitting in a mostly upgraded state. My network was down and network-manager wasn't running so I used network-admin to re-enable eth0 which immediately gave me back network access (still haven't rebooted). I "fixed" a few things that didn't upgrade properly, removed some things I don't really use anyway, and then rebooted.

In general, everything came up fine. I DO have internet access obviously as I'm writing this from the same PC, rebooted to the latest kernel and all the upgrades in place. Actually, it's quite nice so far. The only issue I'm having is that network-manager insists there is no eth0. It will let me add an interface, but if I choose Edit Connections there are none listed under Wired.

By the way, sudo dhclient eth0:
```
There is already a pid file /var/run/dhclient.pid with pid 5711
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:19:21:5b:0c:22
Sending on   LPF/eth0/00:19:21:5b:0c:22
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.199 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.199 from 192.168.0.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 192.168.0.199 -- renewal in 42239 seconds.
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:19:21:5b:0c:22  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fe5b:c22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16758036 (16.7 MB)  TX bytes:1834548 (1.8 MB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4940 (4.9 KB)  TX bytes:4940 (4.9 KB)
```

and yet sudo /etc/init.d/networking restart:
```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
```

Also, if I go into "Network Tools" and choose eth0 from the drop-down it shows everything correctly. However, if I hit configure, it says the interface does not exist.

I really just want to force things back into a "standard state" as if I just re-installed. Then I want to use Jaunty's version of network-manager to set my static IP, etc.

Any help would be great.

---

### Post by ubu-for on 2009-03-13
Look at this thread.

[http://ubuntuforums.org/showthread.php?t=1083934&page=2](http://ubuntuforums.org/showthread.php?t=1083934&page=2)

---

### Post by mattisking on 2009-03-13
That got it. Thanks!

---

