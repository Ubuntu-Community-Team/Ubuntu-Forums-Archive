---
title: "uname question"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by xxxYYY on 2008-02-02
Also posted as sound driver question:
----------------------------------------------
I have a soundBlasterXFi card. Creative labs has a driver which I would like to try, however, the installer seems to require `uname -i` to be x86_64
 
 `uname -m` is x86_64, how do I get `uname -i` to be x86_64?
 
 Or should I change the installer?

---

### Post by Rocket2DMn on 2008-02-03
The -i option, according to the man pages is "Prints the name of the platform."  That doesn't make a whole lot of sense, I think the -m option is what they intended.  It shows that you are using the 64 bit version of Ubuntu and that is what is required by the driver, so you should be OK to install it.

---

