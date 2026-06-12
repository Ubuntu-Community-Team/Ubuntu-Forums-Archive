---
title: "[SOLVED] hplip and apt-get errors after latest update"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by cybergalvez on 2008-02-05
Hi all I hope someone can help me with this.  After the latest round of updates (the kernel update) I am getting these errors with apt-get

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (>= 2.7); however:
  Package hplip is not configured yet.
 hpijs depends on hplip (>= 2.7.12-0ubuntu2~gutsy1); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip-gui:
 hplip-gui depends on hplip; however:
  Package hplip is not configured yet.
dpkg: error processing hplip-gui (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 hplip
 hpijs
 hplip-gui
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Also now the hplip is no longer working

---

### Post by cybergalvez on 2008-02-05
update - I can't print at all, printing is completely broken at this point how can I fix this?
Jose

---

### Post by Scavok on 2008-02-05
Perhaps the answer lies in this recent thread:

[http://ubuntuforums.org/showthread.php?t=687425](http://ubuntuforums.org/showthread.php?t=687425)

---

### Post by cybergalvez on 2008-02-05
> **Scavok said:**
> Perhaps the answer lies in this recent thread:

[http://ubuntuforums.org/showthread.php?t=687425](http://ubuntuforums.org/showthread.php?t=687425)

looked through that post and tried 
sudo dpkg --configure -a
sudo apt-get install -f

which didn't work I still get the same error, kind of afraid to try the other suggestion (deleting some package folder and reinstalling everything) until I get some more pressure to give that a try
Jose

---

### Post by cybergalvez on 2008-02-06
solved see this post for the solution: [http://ubuntuforums.org/showthread.php?t=689046](http://ubuntuforums.org/showthread.php?t=689046)

---

