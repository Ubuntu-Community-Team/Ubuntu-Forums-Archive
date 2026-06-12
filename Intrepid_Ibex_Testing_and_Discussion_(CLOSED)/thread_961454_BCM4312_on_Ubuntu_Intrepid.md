---
title: "BCM4312 on Ubuntu Intrepid"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tiagosc on 2008-10-28
I use Ubuntu Intrepid since version Alpha 5. When i finished installing Intrepid, the wireless works very well, after with some updates, exactly in BETA version (kernel 2.6.27-7) the wireless doesn't work.

> Linux tiago-laptop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

> 08:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

> eth0      Link encap:Ethernet  HWaddr 00:1d:72:64:fa:65  
          inet addr:10.10.6.89  Bcast:10.10.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21d:72ff:fe64:fa65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18797205 (18.7 MB)  TX bytes:2543926 (2.5 MB)
          Interrupt:220 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19920 (19.9 KB)  TX bytes:19920 (19.9 KB)
I can't see my wireless interface

In restrict drivers, where i had activated the "wl" driver, doesn't list this driver more.

---

### Post by Ayuthia on 2008-10-28
You might try the following to see if the system can find the module:
```
sudo updatedb
locate wl.ko
```
If locate returns the module, you can try to load it:
```
sudo modprobe wl
```
If it does not, you might try the following:
```
sudo dpkg-reconfigure linux-restricted-modules-`uname -r`
```
The ` is a backquote and not a single quote.  To test it out so that you have the right one:
```
echo `uname -r`
```
It should return the kernel version.  If it returns uname -r, then you used the single quote.

EDIT: the dpkg-reconfigure hopefully will reinstall the wl.ko module for you.  You might have to go back and enable the driver afterwards.

---

### Post by tiagosc on 2008-10-28
Thanks Ayuthia!
Worked!

Well, this driver "wl" worked, but i don't have support to "monitor mode", since Alpha 5...
It's a bug??

---

