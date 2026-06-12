---
title: "GIMP WONT INSTALL extrmely frusturating"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by superfrogman94 on 2010-10-26
a update (i wish i had not done) removed gimp... so when i try to install it i just get a bunch of helpless errors... i have tried suggestions from others but nothing works...

heres synaptic says:

gimp:
  Depends: libgimp2.0 (<=2.6.10-z) but 2.6.11-1~getdeb1 is to be installed
  Depends: gimp-data (<=2.6.10-z) but 2.6.11-1~getdeb1 is to be installed

but that repository was removed! i even updated after i reomved it so that just dosnt make any sense!!!!!!!:confused:

please help!!!!!!!!! its awful not being able to use gimp...
why does this crazy stuff always happen to me!:(:(:(

---

### Post by jmacn on 2010-11-30
I have the same problem:

$ sudo apt-get install gimp

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: gimp-data (<= 2.6.10-z) but 2.6.11-1~getdeb1~maverick is to be installed
E: Broken packages

---

### Post by lrgmmc on 2010-12-01
have you tried the ppa yet?
[http://www.techtickle.com/install-gimp-2-6-11-ubuntu-10-04-ubuntu-10-10-ppa.html](http://www.techtickle.com/install-gimp-2-6-11-ubuntu-10-04-ubuntu-10-10-ppa.html)
best of luck. :p

---

### Post by lrgmmc on 2010-12-03
did you get it installed?

---

