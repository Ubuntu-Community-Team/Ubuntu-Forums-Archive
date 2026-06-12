---
title: "Nvidia Drivers Causing Kernel Panic"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rfdeshon on 2010-04-07
Just installed Ubuntu 10.04 beta 1 x64 on my MSI EX630 (AMD Turion X2, GeForce 9300M, MCP77 chipset). After the first install, I ran all the updates, installed the nvidia drivers (using the restricted driver manager) rebooted and found that it kernel panicked every reboot no matter which kernel I selected, even if going into single mode. Not a friendly error KP either, a blinking scroll lock/caps lock, no error on the screen kind of KP. 

Wiped, reinstalled, installed only the nvidia drivers (didn't run ANY other updates), same thing. I've never seen a driver cause a KP even when booting into single mode like this. Does anyone have any ideas? I'm at a total loss here.

---

### Post by lidex on 2010-04-07
Try the lucid forum:
[http://ubuntuforums.org/forumdisplay.php?f=377]("http://ubuntuforums.org/forumdisplay.php?f=377")
There are a lot of boot errors with plymouth, mountall, etc. Did you try running a live-session?

---

### Post by rfdeshon on 2010-04-07
You know, I was looking for the beta forums and just couldn't seem to find them. It's been one of those days.

I haven't tried running a live-session, just went straight to install. It boots fine after a clean install, it's only after installing the the proprietary nvidia drivers that it starts kernel panicing on boot.

(Posted this in the appropriate forum: [http://ubuntuforums.org/showthread.php?p=9090617](http://ubuntuforums.org/showthread.php?p=9090617))

---

