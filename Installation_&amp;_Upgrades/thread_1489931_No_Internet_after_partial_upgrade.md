---
title: "No Internet after partial upgrade"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by julz7 on 2010-05-21
Update Manager gave the following message:
```
Not all updates can be installed
Run a partial upgrade, to install as many updates as possible.
This can be caused by:
* A previous upgrade which didn't complete
* Problems with some of the installed software
* Unofficial software packages not provided by Ubuntu
* Normal changes of a pre-release version of Ubuntu
```
with options "Partial Upgrade" and "Close". There were also quite a few updates listed that were unchecked and greyed out.
I ran a partial upgrade. Everything seems fine now except for the tiny little problem that I can't connect to the Internet. It recognizes my wifi network and is connected to it, but I can't actually access anything; everything I try gives a "Server not found" or "Bad hostname" or "Unable to resolve address" error. I also tried FTP and SSH; they don't work. I can't access 192.168.1.1, though 127.0.0.1 works.
(Also if it matters I left Pidgin and Skype open during the partial upgrade.)

---

### Post by julz7 on 2010-05-25
*bump*
I tried running ```
sudo apt-get install -f
``` and ```
sudo dpkg-reconfigure -phigh -a
``` as suggested at [http://shibuvarkala.blogspot.com/2009/12/how-to-recover-ubuntu-after-partial.html]("http://shibuvarkala.blogspot.com/2009/12/how-to-recover-ubuntu-after-partial.html"), but it didn't help.

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:17:31:bf:e7:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2848104 (2.8 MB)  TX bytes:2848104 (2.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:18:f8:ac:fb:f1  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f8ff:feac:fbf1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:255930 (255.9 KB)  TX bytes:924 (924.0 B)
```

---

### Post by rob45 on 2010-05-26
Hi i had this partial up grade thing..i had to run the dpkg-reconfigure a' thing....have you tried running update again?

---

### Post by julz7 on 2010-05-27
I tried a few more things. Connecting the computer directly to the router doesn't work either. However, connecting to the wifi network from a LiveCD works.

---

### Post by julz7 on 2010-06-01
*bump*
I really have no idea what I should do. I haven't been able to find anything else that helps. If necessary I would be able to do a fresh install, but I would really rather not as it is generally a pain in [some arbitrary body part].

---

### Post by julz7 on 2010-06-12
*bump*
So apparently some other people on here have had issues due to partial upgrades that have not been fixable other than with a fresh install. Should I really even bother bumping this thread again if I haven't had any useful responses in some three weeks? Or should I just give up and do a fresh install, even though I would really rather not have to?

---

