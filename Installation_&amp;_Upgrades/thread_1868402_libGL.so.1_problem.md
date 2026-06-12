---
title: "libGL.so.1 problem"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by Diskdoc on 2011-10-24
Hi!

Upgrading Natty -> Oneric went fairly well. I was trying out the Gnome + Cairo thing but was slightly annoyed by some intermittent flickering in Cairo. I wanted to try without the ATI driver and removed it using the Hardware drivers-tool. My machine has an Intel/Radeon GPU combo so I actually have three choices of drivers.

Problem:

No OpenGL-support when booting. I found a clue to the problem, switching to console and running glxgears (I know it wouldn't work, but read on) which complained about not finding libGL.so.1.

I kept nosing around, looking at the update-alternatives-command, ld.so.conf files and so on. I can't seem to find the problem! The only way I get a desktop with 3D support now is by having fglrx installed.

Can someone assist me in fixing the mesa-opengl support?

(edit)

Trying to install libgl1-mesa-glx or libgl1-mesa-dri I get this:

> E: Internal Error, No file name for libgl1-mesa-glx

I might have found the issue in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/859188").

(edit)

Through the posts in the bug report I managed to get libgl1-mesa-glx and -dri reinstalled, but the problem remains. If I remove fgrlx I can't get 3D support from mesa.

(edit)

Solved. Seems these two finally did the trick:

> sudo apt-get remove --purge fglrx*

> sudo apt-get install --reinstall libgl1-mesa-glx:amd64 libgl1-mesa-glx:i386 libgl1-mesa-dri:amd64 libgl1-mesa-dri:i386

---

### Post by sundman on 2011-10-26
Ran into the same problem.

Upgrading an installation that has fglrx to 11.10 breaks libGL links. The key point is to first remove fglrx and then reinstall libl-mesa.

But, I'm glad to finally get rid of fglrx - it has always been a mess.

---

### Post by sundman on 2011-10-26
But, but,

the opensource drivers are far to slow - giving FPS of about 50, so it's rather unusable with compiz.

Had to reinstall it - it made the unity launcher disappear because of conflicting key bindings in compiz. Enabling it in ccsm made it appear.

---

