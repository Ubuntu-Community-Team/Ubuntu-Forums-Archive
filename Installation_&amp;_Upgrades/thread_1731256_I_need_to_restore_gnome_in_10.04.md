---
title: "I need to restore gnome in 10.04"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by th1bill on 2011-04-16
I pulled a bone headed maneuver when I thought I would try KDE.  I used Synaptic and thought that I had done all correctly but on reboot all I got was a BG screen and a terminal wanting me to log in.  I did but remained in the terminal... lost!  I had passed on my 32 bit copy of Lucid so I installed the 64 bit copy on a new partition, so as to recover all my data.  The problem is that the Flash Player does not work and I'm not inclined to fight it into living.  I am downloading the 32 bit copy, right now but I need to know if it is possible to repair my old 32 bit install and save many hours of agony?

---

### Post by Dutch70 on 2011-04-17
When you get to the terminal asking you to login, go ahead and login. Then type...
```
sudo startx
```
If it works, run...
```
sudo apt-get update && sudo apt-get upgrade
```

To get the flash player to work, run this command...
```
sudo apt-get install ubuntu-restricted-extras
```
or install from software center.

---

