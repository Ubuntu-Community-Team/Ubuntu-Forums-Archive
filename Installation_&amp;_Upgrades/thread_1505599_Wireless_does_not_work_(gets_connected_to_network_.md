---
title: "Wireless does not work (gets connected to network successfully though)"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by dineshbabumm on 2010-06-09
Hello Every one,

I just upgraded to 10.04 from 9.10 and I ran into few issues. 
Laptop - Dell Vostro 1520
OS - Ubuntu 10.04 64 bit 

1. My wifi connects to the network properly and shows connection established. But I am not able to browse. I tried ping and I didn't got any response. But I was able to get response when I use ethernet (wired connection) and I am able to browse. No issues with wifi card as my wifi is working properly from Windows and with the same network.

My ifconfig output if that will help:
> 
dinesh@dinesh-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:24:e8:dd:f2:c7
inet addr:192.168.1.5 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::224:e8ff:fedd:f2c7/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:22050 errors:0 dropped:0 overruns:0 frame:0
TX packets:15674 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:29890171 (29.8 MB) TX bytes:1679630 (1.6 MB)
Interrupt:30 Base address:0x6000

eth1 Link encap:Ethernet HWaddr 0c:60:76:09:29:6e
inet addr:192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::e60:76ff:fe09:296e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:47 errors:0 dropped:0 overruns:0 frame:12160
TX packets:60 errors:8 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:15104 (15.1 KB) TX bytes:10512 (10.5 KB)
Interrupt:18

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1696 (1.6 KB) TX bytes:1696 (1.6 KB)

Any suggestions how to get rid of this problem is highly appreciated. Thanks a lot for patiently reading till this and hope that I can get some help in resolving this. :)

---

