---
title: "2 quick problems"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by war-totem on 2005-09-09
just installed ubuntu and already have two problems:
1. no internet.  the cable is plugged in and all that, but no access to the net.  with fedora, it was plug and play.  i dont see why this would be any different.
2. su:  wont accept my password and ive only been asked to input my username and password once while installing.

:(

edit:  scratch the second problem, i was unaware that root login terminal was seperate from terminal.

---

### Post by benash on 2005-09-09
If you want to su, do:
sudo su
then type in your password.  Once you are root, you can change the root's password with passwd if you want.

For the Internet problem, can you show the output of ifconfig?

---

### Post by war-totem on 2005-09-09
ifconfig
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1

do you need any more?

never mind, i figured it out, had to manually detect the ethernet LAN card

just panicked quickly, but im starting to warm up to ubuntu.

---

### Post by benash on 2005-09-09
Is that all you get?  If your ethernet card is detected, you should see another section.  This is mine:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21880 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1995786 (1.9 MiB)  TX bytes:1995786 (1.9 MiB)

ra0       Link encap:Ethernet  HWaddr 00:06:F4:0B:C1:12
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:f4ff:fe0b:c112/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:59845 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9125 errors:9 dropped:9 overruns:0 carrier:0
          collisions:229 txqueuelen:1000
          RX bytes:18257280 (17.4 MiB)  TX bytes:1173104 (1.1 MiB)
          Interrupt:16 Base address:0xc000

The top section is for the loopback device, and the bottom is for my wireless card.  Yours would probably be called eth0 instead of ra0.

---

