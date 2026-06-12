---
title: "Python Idle"
date: 2019-08-31
forum: Installation &amp; Upgrades
---

### Post by daniels2001 on 2019-08-31
Hi! I have a problem with idle-python3.6 . Since I had this problem I unistalled somehow idle and I can't install idle back , and if I try to do 
```
sudo  apt  -fix--broken
```   I get this error :    dpkg: error processing archive /var/cache/apt/archives/idle-python3.6_3.6.8-1~18.04.york0_all.deb (--unpack): trying to overwrite '/usr/lib/python3.6/idlelib/CREDITS.txt', which is also in package libpython3.6-stdlib:amd64 3.6.8-1+xenial1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/idle-python3.6_3.6.8-1~18.04.york0_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

The output of ```
 sudo dpkg --configure -a


 
```
is 
dpkg: dependency problems prevent configuration of idle:
 idle depends on idle-python3.6; however:
  Package idle-python3.6 is not installed.


dpkg: error processing package idle (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 idle


I've tried to dowload the package manually because I found it on a website but it doeyen't work because when I run sudo apt -fix--broken install it installs it automatically

If I try to unistall python , or to install python3.7 it tells me that depends on idle-python3.6 but it's not going to be installed

What should I do??

---

