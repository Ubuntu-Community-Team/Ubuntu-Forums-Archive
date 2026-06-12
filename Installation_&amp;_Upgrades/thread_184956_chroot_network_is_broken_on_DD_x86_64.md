---
title: "chroot network is broken on DD x86_64"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by mwales on 2006-05-30
I upgraded from Breezy to Dapper.  I installed the chroot while it was a Breezy system.  Now that I'm in Dapper, I can't access anything on the net while I'm in the 32-bit chroot.

These are some of the things I've tried:

ifconfig and ping (just regular 64-bit console):
```
mwales@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:7B:2B:ED
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe7b:2bed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3550383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2332233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4967610358 (4.6 GiB)  TX bytes:186387894 (177.7 MiB)
          Interrupt:185 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:943307 (921.1 KiB)  TX bytes:943307 (921.1 KiB)

mwales@ubuntu:~$ ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from google.com (72.14.207.99): icmp_seq=1 ttl=242 time=50.6 ms
64 bytes from google.com (72.14.207.99): icmp_seq=2 ttl=242 time=52.6 ms

--- google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 50.605/51.603/52.601/0.998 ms

``` 
ifconfig and ping (in 32-bit chroot):
```
mwales@ubuntu:~$ dchroot -d
Executing shell in 'hoary' chroot.
mwales@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:7B:2B:ED
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe7b:2bed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3550481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2332323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4967622854 (4.6 GiB)  TX bytes:186395354 (177.7 MiB)
          Interrupt:185 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12391 errors:0 dropped:0 overruns:0 carrier:0


          collisions:0 txqueuelen:0
          RX bytes:943307 (921.1 KiB)  TX bytes:943307 (921.1 KiB)

mwales@ubuntu:~$ ping google.com
ping: unknown host google.com
mwales@ubuntu:~$                      
``` 
I've restarted the networking in the 64-bit console, but that hasn't helped.  I've tried to restart the networking in the 32-bit chroot, but it fails:

```

mwales@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [fail]

``` 
Any ideas on how I can get the network stuff working again for my chroot?

:edit:  Thread title may be a bit misleading.  I'm not saying it's broken in Dapper Drake for everyone, just my system

---

### Post by chrilleh on 2006-08-28
I'm having the same problem now...

---

