---
title: "Wireless Problems: Help Needed"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by urix on 2005-07-20
Hi,

Ive been using and distributing Ubuntu 5.04 for a few months now and have found it absolutely fantastic!

However, today I installed ubuntu onto my sony vaio laptop and to test the wireless features and low and behold it wouldent work. I have tried almost everything but it all takes me the same place, nowhere!

Ubuntu detects my hardware fine, i am using a 3Com Office Connect 11g PCMCIA Card (3CRWE154G72).

All i seem to be getting when trying to ping my Linksys WRT54G router is Destination host unreachable, i have tried everthing and im almost on my last legs!

Any help would be greatly appreciated!

Regards,
Nick Trueman

---

### Post by fizgig on 2005-07-20
I use ndiswrapper on my laptop for my broadcom wireless chip.  Works great.

[http://www.ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper+howto](http://www.ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper+howto)

---

### Post by varunus on 2005-07-20
Can you post the output of "ifconfig" and "iwconfig" in a terminal here?

---

### Post by urix on 2005-07-20
Here are the results from iwconfig and ifconfig:


"lo        no wireless extensions." is worrying me.



root@mobile:/home/nick # iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"awctNET"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:41:9D:CE:79
          Bit Rate:54 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Link Quality=4/0  Signal level=-39 dBm  Noise level=-25 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


root@mobile:/home/nick # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:54:A1:83:08
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:54ff:fea1:8308/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10842 (10.5 KiB)  TX bytes:2394 (2.3 KiB)
          Interrupt:9

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:242042 (236.3 KiB)  TX bytes:242042 (236.3 KiB)

---

