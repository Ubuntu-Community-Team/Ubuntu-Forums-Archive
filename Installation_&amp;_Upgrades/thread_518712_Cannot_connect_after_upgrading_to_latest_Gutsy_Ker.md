---
title: "Cannot connect after upgrading to latest Gutsy Kernel"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by rahimveron on 2007-08-06
I have updated my kernel to Gutsy 2.6.22.9. Now i cannot connect to internet. I have ADSL modem and connect through ethernet.
I can connect to inernet with XP

My ```
ifconfig
``` shows:
```
eth0      Link encap:Ethernet  HWaddr 00:11:11:0D:5E:DB  
          inet6 addr: fe80::211:11ff:fe0d:5edb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6302236 (6.0 MiB)  TX bytes:956749 (934.3 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)
```

I have added the line ```
127.0.0.1 localhost SEBA
```
to my /etc/hosts as was suggested here in the forums.
SEBA is my Box name

---

### Post by Gremlinzzz on 2007-08-06
You did something more than just tried to update the kernel .i updated mine and my system is faster and solid as a rock.desktop 2.6.22-9-generic #1 SMP  have you tried using your default kernels.which you didn't alter.
:guitar:

---

### Post by Gremlinzzz on 2007-08-06
follow the instructions under 
Ok.. Did it hose your box? Too easy.
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
:guitar:

---

### Post by rahimveron on 2007-08-06
> **Gremlinzzz said:**
> follow the instructions under 
Ok.. Did it hose your box? Too easy.
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
:guitar:

I have followed the same instruction on that thread. I used his script to update.
Is there a problem with my codes above like ifconfg  and others
I have added the line 127.0.0.1 localhost SEBA . Is it the mistake. I can connect to the net but not all the time  3 out of 10 tries while it does not happen in XP. Suggest me a solution. 
I am able to get online using live DVD

---

### Post by confused57 on 2007-08-06
Sometimes in Gutsy, I have no internet connection when booting up...opening  a terminal and entering this usually establishes a connection:
```
sudo /etc/init.d/networking restart
```

---

### Post by rahimveron on 2007-08-07
> **confused57 said:**
> Sometimes in Gutsy, I have no internet connection when booting up...opening  a terminal and entering this usually establishes a connection:
```
sudo /etc/init.d/networking restart
```

OK i will try it and confirm.

---

### Post by fredj on 2007-08-08
Boot into the previous kernel, it should still be on your grub menu and see if everything works
again. Are you using ndiswrapper? It often fails with kernel updates and has to be removed and
re-installed.

---

### Post by rahimveron on 2007-08-08
> **fredj said:**
> Boot into the previous kernel, it should still be on your grub menu and see if everything works
again. Are you using ndiswrapper? It often fails with kernel updates and has to be removed and
re-installed.

No i am not using ndiswrapper.

---

### Post by CD Baric on 2007-08-08
Try:

sudo dhcpcd eth0

CD 'Bar' Baric

---

### Post by rahimveron on 2007-08-09
I use this suggestion by stchman about OpenDNS [http://ubuntuforums.org/showthread.php?t=402452&page=5]("http://ubuntuforums.org/showthread.php?t=402452&page=5")and guess what i am online and replying from Ubuntu!!!! High-fives to ubuntuforums.org

---

