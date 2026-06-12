---
title: "Wired connection not recognized"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by Nirva on 2006-12-31
Hellow,

I have Ubuntu edgy on my laptop, and I love it so much that I also wanted to install it on my desktop computer.  There is only one little problem.  When I type iwconfig, there is only this :

lo        no wireless extensions.

wlan0      ....

sit0      no wireless extensions.


So there is no eth0.  This is quite irritating, cause at first I had some problems with my wireless connection, but I couldn't connect to the internet through the ethernet cable because there was no eth0 found.  Does anyone knows how I have to solve this?
Thanks

---

### Post by logos34 on 2006-12-31
linux doesn't seem to detect your ethernet controller.

What do you get with
$ lspci | grep Eth


If you want to find out about a WIRED connection (iwconfig is for wireless) try

$ ifconfig -a
or
$ ifconfig eth0

---

