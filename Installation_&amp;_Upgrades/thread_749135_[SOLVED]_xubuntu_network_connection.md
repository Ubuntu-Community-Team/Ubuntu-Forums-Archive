---
title: "[SOLVED] xubuntu network connection"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by shalemjale on 2008-04-08
I installed X on a computer yesterday (w/ ethernet connected) hoping the system would automatically detect the connection. No luck.
Any suggestions as to how to proceed?

---

### Post by kpkeerthi on 2008-04-08
Run the below commands in a terminal and post the output here?
```
lspci
```
```
ifconfig
```

---

### Post by shalemjale on 2008-04-09
When I try to open terminal to run the commands to get you the info, the computer reboots back to the login screen. ????????

---

### Post by shalemjale on 2008-04-12
Actually, I have managed to load Ubuntu but am still having the problem. The info you asked for (sorry for the delay) is ....
lspci....................
00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03) 
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801AB PCI Bridge (rev 02) 
00:1f.0 ISA bridge: Intel Corporation 82801AB ISA Bridge (LPC) (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801AB IDE Controller (rev 02) 
00:1f.2 USB Controller: Intel Corporation 82801AB USB Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801AB SMBus Controller (rev 02) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801AB AC'97 Audio Controller (rev 02) 
01:0d.0 USB Controller: Silicon Image, Inc. USB0673 (rev 06) 
01:0e.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86) 
desktop:~$ sudo ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:528 (528.0 b)  TX bytes:528 (528.0 b)

---

