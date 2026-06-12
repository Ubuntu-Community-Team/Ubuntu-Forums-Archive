---
title: "Xubuntu unexpectedly ends session (goes to login screen)"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by gersep on 2007-12-19
Hello everyone, 

I need some advice on a Xubuntu installation. I'm trying to install Xubuntu (via the alternate cd, not the live cd) on a 600 Mhz desktop with 256 MB of RAM. The installation runs smoothly and everything installs the way it should, however when running Xubuntu i start getting problems.

Xubuntu loads just fine but when i start working on it, it doesn't let me do much and randomly logs me out of the current session... takes me back to the black screen, displays the "running local boot scripts (/etc/rc.local)" text and then it takes me back to the login screen for me to log in again, this process repeats endlessly and I haven't been able to find a solution on the internet.

Please help me, It's been 3 days since I started with this problem and i can't seem to find a way around this issue. Thank You

---

### Post by gersep on 2007-12-24
Problem solved... I'm posting back in case it can help someone...

On my case i reinstalled on a new hard drive and the problem was solved, but apparently what was going on on the last install was the x-server was crashing... reconfiguring the x-server should do

this can be achieved by going to the "recovery mode" on the booting options and running

> dpkg-reconfigure xserver-xorg

Here you can set the configuration and might help you fix your problem. This helped me fix and issue on another computer where the x-server crashed while trying to load. I hope this can help out a few.

---

