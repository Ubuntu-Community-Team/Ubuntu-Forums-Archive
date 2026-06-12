---
title: "linux-headers-3.13.0-24 package not playing nice"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by jheide44 on 2014-07-12
I've had a rough time playing with apt-get/synaptic & the integrated software update on 14.04, after fixing some missing dependencies via deb's and dpkg there is still one package that seems "hosed beyond my skills"

Breadcrumbs:
```
dpkg: error processing package linux-headers-3.13.0-24 (--configure): package linux-headers-3.13.0-24 is not ready for configuration
 cannot configure (current status `half-installed')

# and later...

Errors were encountered while processing:
 linux-headers-3.13.0-24
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Appears to be a reported bug...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1326640](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1326640)

What do i do now? Has anyone else seen this before?  what new commands do i need to learn, any pointers appreciated.

---

### Post by bapoumba on 2014-07-12
```
uname -a
Linux SonyBlue 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:43:42 UTC 2014 i686 i686 i686 GNU/Linux
```
Current kernel is 3.13.0-30, curious you are on 3.13.0-24.

Have you tried what was recommended in the bug report (adding one additional command to it) ?
```
sudo apt-get install -f
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jheide44 on 2014-07-12
ran those commands... package seemed to hang again... 

then after playing around with the additional repositories and suggested next steps here ([http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr)) the package seems to have installed.

I let it run the upgrade overnight.

in retrospect i probably didn't leave the laptop plugged in the first time.  I may have not plugged in the laptop maybe it went to sleep or ran out of battery causing my original issues.

I will call this a noob error, or patience issue.

Thanks for the help!

---

### Post by bapoumba on 2014-07-13
What would help (at least my understanding ;)) is :
- the exact errors associated to "package hang". Could be many things.
- which additional repos do you have enabled now ?

One thing you need to be aware of. On release upgrades (that is when you'll move from 14.04 to 14.10 or a later release), please remember to disable your third party repos and ppa. That will save you much trouble if you run into a repos that does not have packages for the next version.
If the laptop died in the middle of an upgrade, that may have caused your symptoms. But an update/upgrade cycle should have been enough to fix it (may be a dist-upgrade in that case).

---

