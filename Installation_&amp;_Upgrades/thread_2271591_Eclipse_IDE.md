---
title: "Eclipse IDE"
date: 2015-03-31
forum: Installation &amp; Upgrades
---

### Post by waynemantswe on 2015-03-31
I tried to install Eclipse IDE from terminal and i get message
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Impavidus on 2015-03-31
Usually this means that one of the programs handling package management is either still running or didn't close properly. Check for programs like software centre, synaptic, apt-get and close them. To be sure they are not running, you can reboot. If you still get the same error after rebooting, remove the lock manually:```
sudo rm /var/lib/dpkg/lock
```
On a separate note, you tagged this thread with wubi. Wubi is no longer supported: [http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

