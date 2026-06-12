---
title: "Gutsy Bug - network-manager"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by MMoudry on 2007-12-08
Hi,
I ahve installed gutsy and I am running it on my old Inspiron 8200 laptop that is docked in a docking station (so basically it has three network interfaces, one of which is a wireless card). Every time I try to install new software I get this :

[I]Setting up network-manager (0.6.5-0ubuntu16.7.10.0) ...
 * Reloading system message bus config...
   ...done.
 * Restarting network connection manager NetworkManager
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 2
ldconfig deferred processing now taking place
Errors were encountered while processing:
 network-manager[/I]

The ldconfig deferred processing never ends (I belive a bug report has already been open for this). When it is running it is impossible to start new applications and the network dies. It is even impossible to shutdown the machine although it is not frozen. Only way is to kill the power switch and restart at which point everything works fine again.

Thanks,

MMoudry

---

### Post by ztirffritz on 2007-12-08
Have you found a solution to this problem?  I have a AMD64 laptop and an Intel P4 desktop with the same problem.  It is REALLY annoying.

---

### Post by MMoudry on 2007-12-11
Hmmm ok the problem is solved for me and this is how it happend :

First since every time I had to restart the computer after installing software the package manager got stuck teling me that it is not synced and to execute manually : dpkg --configure --aae (or something like that)

Once I executed that and restarted again it works now.....


MM

---

