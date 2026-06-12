---
title: "Fixing the error with rsync and cupsys"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by hayesha on 2008-05-08
Hi all,

After doing sudo apt-get install <someapp> with gusty giban recently I came a cross that during the installation process it gives the following error and fails the installation. 

```
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing rsync (--configure):
 subprocess post-installation script returned error exit status 1
Setting up cupsys (1.3.2-1ubuntu7.7) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 rsync
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

It would be most helpful if somebody could help me :-( in fixing the issue.
Thanks in advance.

Hayesha.

---

### Post by philg on 2008-05-22
I too am seeing this. I have been digging and can't seem to find any way to get this to stop occuring...

2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
Ubuntu 7.10 

Any clues??? Anyone?  :confused:

---

### Post by kcoylenet on 2008-07-26
Me, too. I even tried to remove cupsys and re-install but I can't remove it because of dependencies. I asked this question on the forum as well, and haven't gotten any answers. I'm also wondering if it is safe to upgrade to Hardy Heron with this error lurking on the machine. I'll let you know if I learn anything.

---

### Post by kcoylenet on 2008-08-20
There are some solutions being offered at:

[http://ubuntuforums.org/showthread.php?t=894480](http://ubuntuforums.org/showthread.php?t=894480)

although so far none have worked for me. But they seem to work for some folks. Worth a try.

---

