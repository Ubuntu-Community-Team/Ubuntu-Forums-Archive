---
title: "Can't Install Skype!"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by jslominski001 on 2007-12-18
I can't install skype.  I download the *.deb file and ran it, I got a message saying:

[COLOR="Red"]Error: Dependency is not satisfiable: libqt4-core[/COLOR]

i tried again running the *.deb file in terminal:

[COLOR="Red"]root@ubuntuser-desktop:/tmp# dpkg -i skype-1.4.0.74.deb
Selecting previously deselected package skype.
(Reading database ... 88064 files and directories currently installed.)
Unpacking skype (from skype-1.4.0.74.deb) ...
dpkg: dependency problems prevent configuration of skype:
skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
dpkg: error processing skype (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
skype
[/COLOR]
so I type in terminal:
[B]
sudo apt-get update[/B]

and 

**sudo apt-get install libqt4-core libqt4-gui**

and i get:
[COLOR="Red"]
root@ubuntuser-desktop:~# sudo apt-get install libqt4-core
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Package libqt4-core is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libqt4-core has no installation candidate[/COLOR]

PLEASE HELP!!!

---

### Post by ellenhidemi on 2007-12-18
I've just installed Skype, and I couldn't do "apt-get install" separately to libqt4-core, libqt4-gui and libaudio2. However,

sudo apt-get install libaudio2 libqt4-core libqt4-gui

works fine.

---

### Post by mikewhatever on 2007-12-19
Can you post the output of the following:
> sudo cat /etc/apt/sources.list

---

### Post by jslominski001 on 2007-12-19
thanks!!

---

