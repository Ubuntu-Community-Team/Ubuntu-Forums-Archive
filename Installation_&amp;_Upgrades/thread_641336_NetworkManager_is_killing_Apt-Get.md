---
title: "NetworkManager is killing Apt-Get"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by ztirffritz on 2007-12-15
Every time that I try to upgrade or install anything apt-get tries to restart NetworkManager for some reason and it fails.  This locks the computer in a weird way.  The mouse still works, but applications won't start and the keyboard is dead so the only option is a hard reset.  Eventually an error is generated saying:
sudo dpkg --configure -a
When I try to do that it locks up.  I've tried to log in remotely using ssh, but the network connect is dead so that doesn't work.  I have two computers with this problem.  One is an AMD64 laptop running Ubuntu 64.  The other is a P-IV Desktop.  It is very frustrating.  I'm getting close to just removing networkmanager and installing WICD.  I've read that even that may be  problem because networkmanager will fail when I try remove it and that will block installation of WICD.

---

### Post by vdbergh on 2007-12-18
I have exactly the same problem. There seems to be no solution except reinstalling. Any help  would greatly appreciated.

---

