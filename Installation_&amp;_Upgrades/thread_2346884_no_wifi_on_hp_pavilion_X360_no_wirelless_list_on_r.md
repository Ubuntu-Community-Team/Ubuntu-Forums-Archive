---
title: "no wifi on hp pavilion X360 no wirelless list on rfkill"
date: 2016-12-19
forum: Installation &amp; Upgrades
---

### Post by rsmpereira89 on 2016-12-19
Hi all 
I installed recently 16.04 on a HP pavilion. I have tried other solutions without success, and I never seen such error in any other forum/post.

The wireless LAN is NOT listed with rfkill[B] 


~$ rfkill list all 

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

[/B][B] ~$ iwconfig
lo        no wireless extensions.

eno1      no wireless extensions.[/B]

[B]
~$  ifconfig

eno1      Link encap:Ethernet  HWaddr d0:bf:9c:8f:0a:11  
          inet addr:192.168.1.79  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8ce6:86f3:e835:4013/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:158684814 (158.6 MB)  TX bytes:4662828 (4.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:159936 (159.9 KB)  TX bytes:159936 (159.9 KB)

[/B]I am 0 at linux, and I would appreciate amy possible help to understand, at least, where is the problem

Thanks

---

### Post by lisati on 2016-12-19
Duplicate of [https://ubuntuforums.org/showthread.php?t=2346882](https://ubuntuforums.org/showthread.php?t=2346882)  closed.

---

