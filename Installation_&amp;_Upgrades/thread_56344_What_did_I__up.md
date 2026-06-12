---
title: "What did I **** up? :/"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by kzu on 2005-08-12
I installed Enlightenment E17 via some HOWTO, then I decided it I didn't like it and i wanted to go back to DR16. So I removed E17, and got new /etc/apt/sources.list without howto's new sources which got me E17. However, sudo apt-get install enlightenment still downloaded new E17, so I used synaptic and force version DR16 for enlightenment, but it didn't work. I once again got new sources.list which should work, but I get this when I try to get enlightenment

sudo apt-get install enlightenment
Reading package lists... Done
Building dependency tree... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate

Well, then I try to get enlightenment-data:
sudo apt-get install enlightenment-data
Reading package lists... Done
Building dependency tree... Done
Package enlightenment-data is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment-data has no installation candidate

what can I do? I just want enlightenment to work :/

---

### Post by wrtrdood on 2005-08-15
Did you remove the entries from /etc/apt/preferences ?

---

### Post by Muffe on 2005-08-26
I have just the same problem as kzu, and do not have a /etc/apt/preferences file... I don't know what I have messed up...

If it's this file that is the reason, can anybody post it here so that i can get it back? Or is it other solutions to this problem?

---

