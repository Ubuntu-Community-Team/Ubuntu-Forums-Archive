---
title: "how to install virtualbox(xp or win7)"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by darkangel_meyou on 2011-02-23
hey guys i'm now on ubuntu and i want to install virtualbox on my system i.e maverick 10.10...........
i downloaded virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_i386.deb but there was a problem
my software center says "Cannot install 'libqt4-network" 
what to do guyz i need you help.....

i even did it with terminal but same prob    'Cannot install 'libqt4-network' 


please help me out guys....

---

### Post by mciverza on 2011-02-23
> **darkangel_meyou said:**
> 
my software center says "Cannot install 'libqt4-network" 
what to do guyz i need you help.....

i even did it with terminal but same prob    'Cannot install 'libqt4-network' 


That sounds like you might have an apt or network connectivity problem.
Try reloading your package lists first.
your system would try to download "libqt4-network ' to satisfy the dependencies of VirtualBox, if the network is down, it won't be able to fetch the package. Or if the package list on your computer is too old, the libqt4-network package may have had a [security/functionality] update and then the old package won't exist anymore.

---

### Post by darkangel_meyou on 2011-02-24
hey thanks man..... It really worked now i can use virtualbox really fine but... still i got a problem i cant use my usb on virtualbox.... can you help me out...................

---

