---
title: "Problems installing Wine"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by cb1993 on 2009-12-16
Hi, I am new to Linux and I am running Mint 8.
I tried installing Wine and got the following message:


[B]******@*******-desktop ~ $ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages[/B] 


Sorry if it is a simple fix but i am not sure of what to do.

---

### Post by x33a on 2009-12-16
please ask this question at mint forums, they'll be able to help you in a better manner.

[http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by MelDJ on 2009-12-16
in terminal try: sudo dpkg --configure -a

---

### Post by cb1993 on 2009-12-16
Thank You

---

### Post by alwayshere on 2009-12-16
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

