---
title: "Failure to start session 14.04 upgrade"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by mike211 on 2014-07-12
I recently upgraded from 12.04 (I think)to 14.04, anywho I can not log in to my account it keeps saying failure to start session. Any advice?

---

### Post by bapoumba on 2014-07-12
There can be many reasons why you cannot start or log into a graphical session.

Can you <ctrl><alt><f1> and get to a virtual terminal ?

If so, please check you are on 14.04 :
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
```

Then :
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get upgrade
```
If you are running one of the flavors, change ubuntu-desktop to kubuntu-desktop or xubuntu-desktop or lubuntu-desktop accordingly.

Then see if <ctrl><alt>f7> brings you back to a working session where you can log in.

You could also be running out of space or inodes or be on an incomplete upgrade, which would require other fixes.

---

### Post by mike211 on 2014-07-12
I can ctr alt f1, but I have tried all those steps sudo apt get update.  It does. Then I sudo apt get ubuntu desktop and it gives me a install -f? I did that and still stuck. I know my password and how to change it in recovery mode so why am I failing to start session? Is 14.04 just a big ole piece of **** cause I haven't been able to log in since the update.

---

### Post by bapoumba on 2014-07-12
Any indication on the errors ? That would help.

---

