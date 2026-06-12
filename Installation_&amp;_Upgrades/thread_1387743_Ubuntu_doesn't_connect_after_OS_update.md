---
title: "Ubuntu doesn't connect after OS update"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by semsaudade on 2010-01-22
Hi to everybody and thanks a lot in advance for your kind help.
I am an absolute newbie, so please use simple words! 

I installed Ubuntu in dual boot with Vista on my PC. First run was OK: Ubuntu started internet connection on my eth0 cable and everything worked smoothly. Then Ubuntu asked me for an update of system: after software download and reboot, eth0 is not recognized anymore! I can't connect to internet, neither with Firefox neither with Synaptic.

Everything is OK with Vista and internet works well from live cd (and all was ok before updating operating system). I read something around about dns problem (I have a belkin modem router) but I wasn't able to understand how to solve the problem,

Is there anybody wishing to help me? Thanks so lot!
Giancarlo

---

### Post by myth1914 on 2010-01-22
from the terminal, try running "ifconfig"  Does it show your card is recognized?

---

### Post by myth1914 on 2010-01-22
Better yet run

lspci

from the terminal and post the output.

---

### Post by semsaudade on 2010-01-23
It is a strange (for me) and random behaviour. This morning, for example, running Ubuntu for the first time, I found internet connection working perfectly (I could surf and download with no problem at all).

However, after rebooting, net connection was unavailable as usual. Sometimes after running Vista on the same PC, net works, sometimes it doesn't.

This is the result of my test, when net is not working:

$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:01.0 Communication controller: Conexant Systems, Inc. SoftV92 SpeakerPhone SoftRing Modem with SmartSP (rev 01)


$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:70:15:f6:cd  
          indirizzo inet6: fe80::221:70ff:fe15:f6cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:100 
          Byte RX:0 (0.0 B)  Byte TX:6128 (6.1 KB)
          Memoria:fdfc0000-fdfe0000 

eth0:avahi Link encap:Ethernet  HWaddr 00:21:70:15:f6:cd  
          indirizzo inet:169.254.10.26  Bcast:169.254.255.255  Maschera:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memoria:fdfc0000-fdfe0000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:240 (240.0 B)  Byte TX:240 (240.0 B)

$ ping [www.libero.it](www.libero.it)
ping: unknown host [www.libero.it](www.libero.it)

$ ping 75.126.162.205
connect: Network is unreachable


I use a Belkin modem router. My network manager in Ubuntu is Wicd. Thanks a lot for your kind help!

Giancarlo

---

