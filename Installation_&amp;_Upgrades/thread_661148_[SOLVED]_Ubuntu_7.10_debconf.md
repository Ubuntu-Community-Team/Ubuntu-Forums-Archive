---
title: "[SOLVED] Ubuntu 7.10 debconf"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by Bliepo32 on 2008-01-07
Recently, I tried installing xubuntu 7.04 on my old (read: ancient) laptop. It failed however, and I gave up.

Now xubuntu 7.10 is here, I decided to have another go. I downloaded the cd, burned it, and started the install. The first part goes ok, and then, suddenly, the screen turns blank. When I push Ctr + Alt + F4 (tty4), I see the following happening:

Quote:
[date and time] debconf: Setting debconf language to en
[date and time] init: Process '/sbin/debian-installer' (pid: [the pid]) exited. Scheduling it for restart
[date and time] init: Starting pid [the pid], console /dev/tty1: '/sbin/debian-installer'
This message keeps repeating itself over and over again.

System specs
========
Laptop: Compaq Armada 1592DT
Processor: Intel Pentium MMX 233 MHz
Data bus speed: 66 Mhz
Cache memory: L2 Cache - Write-Back - 512 KB
RAM: 32MB EDO RAM
Hard Drive: 3.2 GB (I use a USB-stick as an extra external drive)
Video Memory: EDO RAM - 2 MB
Supported Display Graphics: VGA ( 640x480 ), XGA ( 1024x768 ), SVGA ( 800x600 ), SXGA ( 1280x1024 )

---

### Post by wolfen69 on 2008-01-07
from your system specs i can see you do not have enough horsepower to run xubuntu. the only thing that might work is to do a command line install of ubuntu and put openbox or fluxbox desktop environment on it. [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

or you could put Damn Small Linux on it. (even better yet) [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by Bliepo32 on 2008-01-07
thanks.

---

