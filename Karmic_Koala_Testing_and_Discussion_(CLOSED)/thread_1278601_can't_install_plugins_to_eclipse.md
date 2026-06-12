---
title: "can't install plugins to eclipse"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by frankabel on 2009-09-29
Hi all,

When start eclipse the following message appear:

"This Eclipse build doesn't have support for the integrated browser"

Then, after click on "OK", and go to "Help->Software Updates..." the following message appear:

"Cannot launch the Update UI. This installation has not been configured properly for Software Updates".

What I need is install pydev to use eclipse to programming in python like [http://pydev.org/manual_101_install.html#id2](http://pydev.org/manual_101_install.html#id2) . Any help?

I really don't found the " Install New Software..." or "Find and Install" menu.

Cheers
Frank Abel

---

### Post by cdahmedeh on 2009-09-29
Yes, I noticed that eclipse won't install under karmic. Seems to be some sort of dependency problem.

---

### Post by lean on 2009-09-30
This is easy to answer. Eclipse is not supposed to be installed using the package manager, since in that case, only root can install plugins.

Download Eclipse manually and you will be happy.

Note this is a problem in all distributions, and you can try too google it, and the answer will probably be 'download and install it with your user'. This is also the reason that Eclipse in distributions are older versions, since nobody sees a point in updating them.

In the future it could be possible that a Eclipse could have the plugins installed per user, but this is not the case yet.

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by Awareness on 2009-10-21
thanks i had the same problem :D

---

### Post by SevenMachines on 2009-10-21
> **lean said:**
> This is easy to answer. Eclipse is not supposed to be installed using the package manager, since in that case, only root can install plugins.
...
In the future it could be possible that a Eclipse could have the plugins installed per user, but this is not the case yet.


The problem was the result of 
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/438414](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/438414)

which should be fixed in 3.5.1-0ubuntu7
Eclipse has had per user plugin support (location of plugins outside eclipse installation root) for some time, helpful to keep plugins maintained over upgrades to a new version of eclipse. If you add something like the pydev update site to karmic repository eclipse then it is installed to ~/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/

---

