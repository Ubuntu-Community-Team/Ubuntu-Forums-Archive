---
title: "Dell Inspiron 500m won´t connect to internet!! HELP!?!?"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by andrenos on 2005-09-13
I´ve just installed Ubuntu on my Dell Inspiron 500m laptop. But it won´t connect to internet!!
In this laptop it´s a wireless ethernet-card, and I want to take advantage of the wireless network here.
I think i´ve connected to the wireless-network, but again, I can´t go online.
I lauch Connection Properties, and there is the connection "eth0" activated. But the status switches from Idle to Receiving all the time. The signal strength is almost 100%.

In the properties for "eth0", i´ve wrote the ESSID and the WEP-key for the wireless network. In the Connection Settings i´ve choosed Static IP address, the IP address and Subnet mask is ok, and the Gateway address is clear.

When i write ifconfig in the Terminal, I get this result:
> ifconfig 
eth0 
Link encap:Ethernet HWaddr 00:04:23:65:AB:D4 
inet addr:192.168.2.101 Bcast:192.168.2.255 Mask:255.255.255.0 
inet6 addr: fe80::204:23ff:fe65:abd4/64 Scope:Link 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:1 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) 
Interrupt:5 Base address:0x8000 Memory:fcfff000-fcffffff 

lo 
Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:164 errors:0 dropped:0 overruns:0 frame:0 
TX packets:164 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:13450 (13.1 KiB) TX bytes:13450 (13.1 KiB) 

Can someone help me? PLEASE!!

(i´m sorry for the bad english, but i´m norwegian :-P)

---

### Post by sir_mud on 2005-09-13
hmm, thought i had already replied to this post, is it a centrino notebook or are you using a pcmia card for wifi and if so what brand

---

### Post by andrenos on 2005-09-14
Yes, you`ve already replied to this post, but [this](http://ubuntuforums.org/showthread.php?t=65329) is the right post.

Please reply [here](http://ubuntuforums.org/showthread.php?t=65329) :)

---

