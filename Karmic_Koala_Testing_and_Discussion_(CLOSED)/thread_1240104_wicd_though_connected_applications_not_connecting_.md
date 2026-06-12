---
title: "wicd though connected applications not connecting to internet"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jithin1987 on 2009-08-14
I installed wicd on my karmic alpha 4. Though from the wicd controller window I can see my wired or wireless connection getting connected none of my applications can connect to internet. 

Even ping don't work. I use kubuntu alpha 4 . Is anyone using wicd? Please help.

---

### Post by zenarcher on 2009-08-14
I'm not sure exactly what to tell you, but I'm using Kubuntu 9.10 Alpha with all the current updates and using wicd.  I could not get a wireless connection with network manager until I switched to wicd.  Since I installed wicd, my wireless has been working just fine, even with all the current 9.10 updates.  I was pretty frustrated with the wireless situation until I read a post here on the forum suggesting that we try wicd.

Cheers,
zenarcher

---

### Post by jithin1987 on 2009-08-14
> **zenarcher said:**
> I'm not sure exactly what to tell you, but I'm using Kubuntu 9.10 Alpha with all the current updates and using wicd.  I could not get a wireless connection with network manager until I switched to wicd.  Since I installed wicd, my wireless has been working just fine, even with all the current 9.10 updates.  I was pretty frustrated with the wireless situation until I read a post here on the forum suggesting that we try wicd.

Cheers,
zenarcher

The wicd client shows network as connected, tried both wireless and wired. But for some reason no application can connect.

So I am currently stuck with network manager and network-manager-gnome.
knetworkmanager that comes with karmic is useless, it does not connect to any wireless.

---

### Post by slakkie on 2009-08-14
If wicd says you are connected, can you post the output of ifconfig -a, netstat -rn

---

### Post by jithin1987 on 2009-08-14
ifconfig -a                                                                                                                          
eth0      Link encap:Ethernet  HWaddr 00:1b:38:7c:fe:b6                                                                                                      
          UP BROADCAST MULTICAST  MTU:1500  Metric:1                                                                                                         
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                                                                                                 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                                                                               
          collisions:0 txqueuelen:1000                                                                                                                       
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                                                                                             
          Memory:e4600000-e4620000                                                                                                                           

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2920 (2.9 KB)  TX bytes:2920 (2.9 KB)

pan0      Link encap:Ethernet  HWaddr fe:31:a5:2b:78:5e
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0ifconfig -a                                                                                                                          
eth0      Link encap:Ethernet  HWaddr 00:1b:38:7c:fe:b6                                                                                                      
          UP BROADCAST MULTICAST  MTU:1500  Metric:1                                                                                                         
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                                                                                                 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                                                                               
          collisions:0 txqueuelen:1000                                                                                                                       
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                                                                                             
          Memory:e4600000-e4620000                                                                                                                           

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2920 (2.9 KB)  TX bytes:2920 (2.9 KB)

pan0      Link encap:Ethernet  HWaddr fe:31:a5:2b:78:5e
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:79:99:ed
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe79:99ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28441222 (28.4 MB)  TX bytes:3553243 (3.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-79-99-ED-37-39-00-00-00-00-00-00-00-00
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:79:99:ed
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe79:99ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28441222 (28.4 MB)  TX bytes:3553243 (3.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-79-99-ED-37-39-00-00-00-00-00-00-00-00
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

---

### Post by slakkie on 2009-08-14
I think something went wrong with the c/p (btw, output like this is best preserved in [code] tags)

Can you ping your gateway? 192.168.1.1? If so, can you ping your nameserver (grep nameserver /etc/resolv.conf, and ping the one), of so, ping a host, eg google.com.

If you don't have nameservers defined, then that is your problem. You need to define them. Don't know how wicd works, but it should be an option somewhere.

---

### Post by jithin1987 on 2009-08-14
knetworkmanager was updated yesterday and now can connect to wireless networks. So gonna stick with it for now.
Thanks guys for trying to help me out.

---

