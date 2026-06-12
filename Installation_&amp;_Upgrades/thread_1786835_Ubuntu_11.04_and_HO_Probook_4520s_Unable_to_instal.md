---
title: "Ubuntu 11.04 and HO Probook 4520s: Unable to install"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by luberfly on 2011-06-20
Dear friends,
I tried to install on my laptop HP Probook 4520s with ATI Radeon i915 video card the Ubuntu 11.04 but it seems impossible to do it.
The laptop make the boot from USB or CD live, but after a few second will remain stopped on pink ubuntu screen or black screen.

It is possible to bypass the problem?

How I can fix it?

Bets Regards

Luca

---

### Post by mörgæs on 2011-06-21
There are some links in the top of this post:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)
They have helped a lot of others.

---

### Post by maozza on 2011-06-29
I had the same problem while upgrading from 10.4 to 10.10 (now I'm running 11.04)
I resolved it by 
1. temporary disabled the wireless card on bios, start the OS.
2. echo "blacklist rt2800pci" >>/etc/modprobe.d/blacklist.conf
3. and enable it again.


some info: [http://ubuntuforums.org/showthread.php?t=1592731](http://ubuntuforums.org/showthread.php?t=1592731)

hope it helps

---

