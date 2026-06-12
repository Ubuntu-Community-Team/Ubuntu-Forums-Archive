---
title: "Wifi too slow"
date: 2009-05-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ytorres on 2009-05-23
Hi all,

I have a strange problem.

When I just reboot, my wifi connection is correct.
I use ndiswrapper, my wifi card is :

```

03:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

And as long the time gone, my connection is more and more slow.

When I just reboot, my connection is about 800 Ko/s.
After about 5 minutes, my connection is about 400 Ko/s.
After about 15 minutes, my connection is about 80 Ko/s.

I search around and didn't find what's up with this...

I have disable ipv6, same problem.
I have change the ndiswrapper's driver, same problem.

I suspect the 2.6.30-5 kernel.

Perhaps with an older kernel.... must test this idea.

So. Anyone have this strange behaviours ?

Best,
Yannick

---

### Post by Ytorres on 2009-05-23
Just testing with Kernel 2.6.28-11.

All is fine. Connection is now always Ok.

Must wait to a kernel update to see if this problem was fix.

---

### Post by tad1073 on 2009-05-23
same problem here, but mine starts slow and stays slow.

[http://ubuntuforums.org/showthread.php?p=7332910#post7332910](http://ubuntuforums.org/showthread.php?p=7332910#post7332910)

---

