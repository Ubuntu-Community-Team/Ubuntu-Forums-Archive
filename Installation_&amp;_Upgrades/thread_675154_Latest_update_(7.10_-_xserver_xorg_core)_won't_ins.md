---
title: "Latest update (7.10 - xserver xorg core) won't install"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by havfunonline on 2008-01-22
Xserver-xorg-core

whatever it is, the update for it won't install every time I try it, it gives the following error message:

"W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb)
  Could not resolve ‘security.ubuntu.com’"

Help please?

---

### Post by dstickst on 2008-01-30
I have the same problem. It's really annoying that the Update Manager keeps popping up just for that FUBARed update.

---

### Post by Shazaam on 2008-01-31
dstickst......
A tip to disable updates for certain apps=
Open Synaptic; find the offending file, highlight it.
Go to Package>Lock version; check it off.
Use this as a temporary work-around as most of the updates are usually security related.

The only thing that was broken was that the update removed a symlink causing 3d and opengl apps to break. Here is a page with a fix for the problem.......

[http://ubuntuforums.org/showthread.php?t=671091&highlight=glxinfo](http://ubuntuforums.org/showthread.php?t=671091&highlight=glxinfo)

Post #6 by oscarsfriend.

---

