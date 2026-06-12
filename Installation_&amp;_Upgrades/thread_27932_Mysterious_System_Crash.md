---
title: "Mysterious System Crash"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by jkndrkn on 2005-04-18
I've managed to set up a wireless connection using ndiswrapper, I've managed to get sound (partially) working, and I've managed to fully upgrade my packages to the latest releases via apt-get.

However, my system suffers from a strange crash. Without warning, everything will hang, the image on the monitor will freeze, and the keyboard and mouse stop working. I have to power off to recover.

I've tested this by using many many applications, and by booting up, not starting up anything in gnome and not even connecting to the internet. Either way, the system eventually hangs.

Where can I begin diagnosing this problem? I've heard of people referring to system logs, but I'm not sure what the best path to take is.

Could someone point me in the right direction?

Thanks.

---

### Post by NaplesBill on 2005-04-18
It sounds like you have an Nvidia video chipset.  I had a motherboard with built-in nvidia chipset and I had to use the "vesa" driver instead of the "nv" or "nvidia" chipsets.  That's the only thing that worked for me.

---

### Post by jkndrkn on 2005-04-18
How does one change to the vesa driver? Does this involve a lengthy kernel compilation process? I found a post that seems to describe a similar procedure.

[http://ubuntuforums.org/showthread.php?t=21554&highlight=installing+graphics+driver](http://ubuntuforums.org/showthread.php?t=21554&highlight=installing+graphics+driver)

Where do I begin?

Thanks.

---

### Post by jkndrkn on 2005-04-20
Looks like the the "nv" and "nvidia" drivers in xorg.conf are the culprit. My system runs smoothly now, but without good graphics support, since the vesa driver is pretty weak.

At least there is no more crashing.

---

