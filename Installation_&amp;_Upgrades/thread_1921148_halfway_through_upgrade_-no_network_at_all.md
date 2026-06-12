---
title: "halfway through upgrade -no network at all"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by emamm2008 on 2012-02-06
Hello

When upgrading to 11.10, somehow the install process got stuck at some level and I stupidly rebooted the system. As a result I have now a partially installed upgrade with no network, no updated kernal and probably more issues that I am not aware of.  

I have tried cdromupgrade but the program sends out a msg that the system does not need upgrade.

I have also tried apt-get update (just the cdrom) but Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused comes out.

Is there a way to sort this out without a fresh install?  I do not want to wipe out home.

Many thanks.

Ed

---

### Post by searchfgold6789 on 2012-02-06
This command should do the trick:```
sudo dpkg --configure -a
```

---

### Post by emamm2008 on 2012-02-06
Unfortunately it did not work. After the command dpkg, I tried sudo apt-get update but the same error msg come out (socket: connection refused).  

It seems that I need to get the network working but I do not know how.


Is home wiped out if a fresh install (disk usage in manual - no format) is attempted?

Many thanks

Ed

---

### Post by searchfgold6789 on 2012-02-06
If you do a fresh install , all the data in your home folder will be erased, unless you have it backed up somewhere.

---

