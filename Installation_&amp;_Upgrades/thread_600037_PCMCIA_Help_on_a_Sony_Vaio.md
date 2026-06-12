---
title: "PCMCIA Help on a Sony Vaio"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Duroon on 2007-11-01
I installed Gutsy on an older Vaio (PCG-V505AX model) and everything seems to be working fine except the PCMCIA slot. No card I insert seems to be recognized. I am rather new to the whole Linux experience and am hoping someone can tell me what I need to do to get the slot turned on as the laptop has no wireless NIC built into it. I have a PCMCIA wireless NIC to use.

---

### Post by Pumalite on 2007-11-01
I don't know if this will help understand the problem:
[https://bugs.launchpad.net/ubuntu/+source/pcmcia-cs/+bug/15408](https://bugs.launchpad.net/ubuntu/+source/pcmcia-cs/+bug/15408)

---

### Post by Duroon on 2007-11-02
Unfortunately no that didn't help. I did manage to track down some info saying that the pcmcia hardware in various Sony Vaio's just doesn't work yet with the new kernel. Guess I am going to have to break down and buy a USB wireless NIC after all.

---

### Post by Pumalite on 2007-11-02
Good luck.

---

### Post by Duroon on 2007-11-02
I picked up a D-Link WUA-2340 usb 802.11G wireless adatper and after a few restarts of the system it works fine. It is not listed as one of the adapters that works with Linux on the various hardware sites but using the ndiswrapper it does indeed work with Ubuntu 7.10.:)

---

### Post by Pumalite on 2007-11-02
Great for you!

---

### Post by Duroon on 2007-11-02
Thanks, I even have a quick screenshot to show that I can see 4 more wireless networks that none of my other computers have picked up lol.

[[IMG]http://img211.imageshack.us/img211/4519/screenshotaz6.th.png[/IMG]](http://img211.imageshack.us/my.php?image=screenshotaz6.png)

---

### Post by Pumalite on 2007-11-02
Nice.

---

