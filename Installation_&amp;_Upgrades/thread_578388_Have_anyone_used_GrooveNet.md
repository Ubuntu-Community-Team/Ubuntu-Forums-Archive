---
title: "Have anyone used GrooveNet?"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by nikola17681 on 2007-10-17
I need help to instal it.

[http://www.andrew.cmu.edu/user/rahulm/Research/GrooveNet/](http://www.andrew.cmu.edu/user/rahulm/Research/GrooveNet/)

I have to open the project within KDevelop.

When I try to build the project the answer is this one:

make: *** No rule to make target `/usr/lib/qt3/mkspecs/default/qmake.conf', needed by `Makefile'. Stop.

What do I have to do?

I have to copy this file:

copy the qt default settings file (you need root access for this)
cp groovenet/docs/groovenetrc /usr/lib/qt3/etc/settings

If I have no the folder /etc/setting, 

Can I do?

Thanks.

---

