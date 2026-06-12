---
title: "Dapper To Edgy Xorg Crashes"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by lesliem on 2006-10-27
HI Everybody,
Tried upgrading from Dapper to Edgy using Synaptic, changed repositories, all seemed well till re-boot.  Splash screen worked then no GUI, on command line tried dpkg reconfigure but no go.
 Says xorg not installed or broken!!!
If I remember xfree crashing happened at Dapper launch.
Any Ideas!!!
My Hardware is AMD 64 Mother/B ASUS A8N-SLI
VIDEO PCI-E Nvidia] 7800GT
](*,)

---

### Post by spacepluk on 2006-10-27
I've the same problem,
I'm getting the forums through console and lynx... :(

---

### Post by uranus65 on 2006-10-27
I initially had the same problem.  My system would just boot to command prompt.  I renamed /etc/X11/xorg.conf to /etc/X11/xorg.conf.old. Then I took what I assumed to be a back-up which was /etc/X11/xorg.conf.2006... and renamed it /etc/X11/xorg.conf and rebooted.  This time I still got some weirdness but login screen came up.  The only problem that I seem to be having now is that my USB Wacom tablet no longer works.  I had to plug in a PS/2 mouse.

---

### Post by viper on 2006-10-27
[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)
Check this thread out.:)

---

