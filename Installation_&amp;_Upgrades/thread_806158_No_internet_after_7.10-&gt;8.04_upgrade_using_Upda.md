---
title: "No internet after 7.10-&gt;8.04 upgrade using Update Manager"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by adrian_ang on 2008-05-24
Hi All,
thanks for sharing your time.

I have a dual boot personal computer Kubuntu/Windows XP. This computer uses a wired internet connection through a router. The router also configures DHCP settings of the host.

There was no problem with Kubuntu 7.10 and Windows XP internet access until I upgraded Kubuntu 7.10 to 8.04 using Update Manager.
After this upgrade there is no internet access using Kubuntu 8.04. While using Kubuntu 8.04 I'm able to verify that DHCP settings are done by the router:

$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:56:98:73
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe56:9873/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3030 (2.9 KB)  TX bytes:3854 (3.7 KB)
          Interrupt:22 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1332 (1.3 KB)  TX bytes:1332 (1.3 KB)

$

but when I try to ping the router :

:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted


ping: sendmsg: Operation not permitted

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

$

While using Windows XP I can ping it successfully and there are no problems with internet.
While using Windows XP I'm able to access router's web interface
[http://192.168.1.1/](http://192.168.1.1/)
but when I try it from Konqueror with Kubuntu 8.04 I get:

[http://192.168.1.1/](http://192.168.1.1/)
An error occurred while loading [http://192.168.1.1/:](http://192.168.1.1/:)
Could not connect to host 192.168.1.1.

I was able to access this interface while I was using Kubuntu 7.10


Please, help to resolve this issue. Any help appreciated.

Thanks in advance.

---

### Post by xfceuser on 2008-05-24
see if you are using a Firewall in KUbuntu.

---

### Post by adrian_ang on 2008-05-25
Hi, thanks 

after issuing :

$ sudo ufw disable && sudo ufw status
Firewall stopped and disabled on system startup
Firewall not loaded
$

everything seems to work now.


> **xfceuser said:**
> see if you are using a Firewall in KUbuntu.

---

