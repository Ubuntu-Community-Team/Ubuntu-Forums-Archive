---
title: "No Network after 10.04 upgrade"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by coconut153 on 2010-05-21
Hi all

I was using Karmic Koala on my Asus 1005HA and everything was working ok. After upgrading to Lucid Lynx I have no network access anymore.

Pinging to my router returns "Network is unreachable".

¿any ideas?

Thanks in advance.

---

### Post by mionescu on 2010-05-21
Can you give more details? Wireless or wired connection? If wireless, what card do you have? Can you see any connection in NetworkManager?

---

### Post by coconut153 on 2010-05-21
Thanks for reply.

Sorry, I'm talking about wired connection. I can see Auto eth0. It says "never" in the field Last Used.

Regards.

---

### Post by mionescu on 2010-05-21
I think it safe to ingnore the "never" used part (it always shows that for me and my wired connection works just fine). 

Can you give the information provided if you right-click on NetworkManager and select "Connection Information"? Alternatively, if you preffer the terminal, just post the outcome of command
ifconfig

---

### Post by coconut153 on 2010-05-21
Sure. This is the ifconfig output:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


TIA

---

### Post by allmedia on 2010-05-21
I have (almost) the same problem except that the upgrade never completed. I got green ticks up until the reboot then GRUB went to ASH reporting the error cannot mount blah, net sockets not available, netdev [900] etc.
I then worked around with a 10.04 cd boot. that seems to connect on everything but Port 80. Ping is slow but works, Tracert works (to external destinations). The 8.04 cd works fine. It suggests there has been some change in the way 10.04 talks to my very ordinary (old) wired ADSL/router but I have absolutely no idea what it is.:confused:
This was never a problem before with ubuntu - in fact it was its main attraction. Ironically I am seriously considering going back to Windows.

---

### Post by coconut153 on 2010-05-21
May be something related with the Netmask?

I'm saying this because the one it appears in ifconfig is 255.0.0.0. However, It's 255.255.255.0 in Network Connections, but I cannot change it from  there. When I try to change it in the IPV4 Settings tab, it becomes 255.255.255.0 again.

Sorry but my linux knowledge is very limited.

---

### Post by mionescu on 2010-05-21
This is weird. It seems that ubuntu does not load the driver for your network card. Can you post the outcome of the following command
dmesg | grep eth

I hope that this would show if there is any problem with the driver. Do you have, by any chance, a different version of the kernel you can boot in (in the loggin menu) and compare the outcome of the same command? I did have a similar problem on my laptop when updating from 9.04 to 9.10 and I solved it by installing backports modules. But I had a wireless card. 
You might need to fill in a bug report if we don't figure it out.

allmedia I think your problem is completely differet and I would advise you to open a new thread.

---

### Post by coconut153 on 2010-05-21
Sure. This is the dmesg | grep eth output:

[   13.742018] eeepc_laptop: Get control methods supported: 0xe101713

Thanks anyway

---

### Post by mionescu on 2010-05-21
This does not say anything to me. Can you post the specifics of your computer (desktop/laptop, type and some hardware information). Maybe someone with a similar computer can help. Did you try to Ubuntu live cd before (or after) the update to check if the internet connection works?

---

### Post by coconut153 on 2010-05-21
Sorry, it's a Asus Eee PC 1005 HA. It's a netbook.. No CD.

Maybe I will go back to Karmic Koala, it was working pretty good... 

Thanks a lot

---

### Post by mionescu on 2010-05-21
You can run the live Ubuntu on an usb stick then. Try that first and see if everything works. . Or try one of the  Ubuntu derivatives designed for netbooks (the Netbook remix, eeebuntu [http://www.eeebuntu.org/](http://www.eeebuntu.org/)). If nothing else works then it would be a good idea to go back to KK

Good luck.

---

### Post by coconut153 on 2010-05-21
Ok. I will try. 

Thank a lot for your time. ;)

---

