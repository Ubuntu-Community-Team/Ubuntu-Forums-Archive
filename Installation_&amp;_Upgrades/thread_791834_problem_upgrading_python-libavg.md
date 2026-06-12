---
title: "problem upgrading python-libavg"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by drkitty on 2008-05-12
Update Manager keeps *telling* me that an upgrade is available for python-libavg_0.7.0-4ubuntu1_i386.deb. When I *tell* it to go ahead and install it provides an error message: 

E: /var/cache/apt/archives/python-libavg_0.7.0-4ubuntu1_i386.deb: subprocess pre-installation script returned error exit status 1

When I use apt-get install libavg I get:

Preparing to replace python-libavg 0.6.0-6build1 (using .../python-libavg_0.7.0-4ubuntu1_i386.deb) ...
pycentral: pycentral pkgprepare: not overwriting local files
pycentral pkgprepare: not overwriting local files
dpkg: error processing /var/cache/apt/archives/python-libavg_0.7.0-4ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-libavg_0.7.0-4ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can someone tell me what's happening here and how to fix it? 
](*,)

---

### Post by Virgil Jones on 2008-10-01
I have the same problem described here. It came about when I tried to upgrade my system.  My system keeps telling me to install Python-libavg.
When I attempt to install it an error occurs.  The research I have done makes it appear that a lower level is received to install than is installed on my system.  Can someone let me know how to resolve this?

---

### Post by drkitty on 2008-10-02
I ended up just uninstalling python-libavg with synaptic.  It's been a year and no problems. Doens't seem to be that critical to most apps.

---

