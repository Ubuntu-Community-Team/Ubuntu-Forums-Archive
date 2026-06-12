---
title: "broken packages error trying to install gnome-core"
date: 2015-02-23
forum: Installation &amp; Upgrades
---

### Post by T.Williams on 2015-02-23
I am fairly new to Ubuntu, and I am stumped for how to fix this.  Please help.   I did the following sequence of steps:

$ sudo apt-get update

$ sudo apt-get install gnome-core

I got :
The following packages have unmet dependencies:
 gnome-core : Depends: gdm (>= 3.4) but it is not going to be installed
              Depends: gnome-control-center (>= 1:3.4) but it is not going to be installed
              Depends: gnome-packagekit (>= 3.4) but it is not going to be installed
              Depends: gnome-session (>= 3.4) but it is not going to be installed
              Depends: gnome-settings-daemon (>= 3.4) but it is not going to be installed
              Depends: gnome-shell (>= 3.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Based on searching for similar issues, I tried :
$ sudo apt-get install -f 
$ sudo dpkg --configure -a
$ sudo apt-get autoremove
no errors with those steps, but it didn't help.  I tried manually installing the packages that were listed as having unmet dependencies, but they came up with even more unmet dependencies. 

 My version info:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

I recently accepted the updates Ubuntu has been telling me to install.  Suggestions?

---

### Post by ian-weisser on 2015-02-23
The package manager is probably working fine.
The most likely cause is that you have (unknowingly) told the package manager to do something utterly impossible.

So we need to figure out what the impossible assumption is.

Please post the output of the following commands:
```
uname -r
apt-cache policy gdm
```

---

