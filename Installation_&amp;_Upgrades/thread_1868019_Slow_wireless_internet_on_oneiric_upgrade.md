---
title: "Slow wireless internet on oneiric upgrade"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by v923z on 2011-10-23
Hi All,

I have just upgraded from natty to oneiric, and my wireless internet is extremely slow, and intermittent. I found that it might be related to the new kernel. However, the links that I have come across concern a Realtek controller, see e.g., 
[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)
[http://russell.ballestrini.net/r8168-driver-issues-after-ubuntu-11-10-upgrade-kernel-linux-3-0/](http://russell.ballestrini.net/r8168-driver-issues-after-ubuntu-11-10-upgrade-kernel-linux-3-0/)
[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal)

I haven't that. The output of my lspci is
```

root@penguin:src# lspci | grep Net
04:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
07:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

```
thus, I conclude that I have an intel controller:) My question is whether anyone knows how to fix this issue. I have to admit I haven't searched the forum very exhaustively, for the simple reason that my internet connection is slow, and intermittent. However, I did search the net looking for an answer. Anyway, if someone could point to a solution, I would be rather grateful. I have a lenovo G550 64-bit computer, if that matters.
Cheers,
v923z

---

### Post by Chemtox on 2011-10-23
You may want to use a search engine next time you search the net.  Helps a lot, found several answers immediately. ;)

Usually a problem with 11n and/or NetworkManager:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/836250](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/836250)

Cheers.

---

### Post by v923z on 2011-10-24
> **Chemtox said:**
> You may want to use a search engine next time you search the net.  Helps a lot, found several answers immediately. ;)


Yes, that is absolutely true, but perhaps, you should reckon that I am not running the google servers, that is to say, in order to use a search engine, one needs a working internet connection:) In would be much easier, if I had the whole internet in my cache... But thanks for the answer!
Cheers,
v923z

---

