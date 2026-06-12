---
title: "Upgrade to 5.10 breaks Moneydance?"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by gila_monster on 2005-11-29
I upgraded from Hoary to Breezy not long ago, and there's apparently some change in the Java engine install that breaks Moneydance now. Has anyone else had this problem? What did you do to fix it? I played around a bit today, but didn't make much headway (lack of time, mostly).

Thanks.

gm

---

### Post by amohanty on 2005-11-29
sun jre is no longer available on 5.10 repos. maybe gij broke it? what vm did you use on hoary?

you can get the sun jre from the plf repos:
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

remember to uninstall gcj and gij


HTH
AM

---

### Post by gila_monster on 2005-12-01
Okay, got a fix from the Moneydance crew. Fairly straightforward, here's what worked.

In the directory in which Moneydance is installed, you need create a link to the directory where your Java executable resides.

Example:

 %> cd /usr/local/moneydance <or other directory where you installed>
 %> rm jre
 %> ln -s /usr/j2se jre <or other Java executable>

Where /usr/j2se/bin/java is the Java executable. Note that you are making a link only to the top level directory, not to the bin directory or to the executable itself.

The good part of this is that you don't need to uninstall the other Java libs, which means that you don't risk breaking other applications.

gm

---

