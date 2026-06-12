---
title: "Aptitude Error: CLVM"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by leebrent on 2007-05-24
Hey There,

I am trying to install a packge with aptitude, and I get the following error: 

leeb@leeb-laptop:~$ sudo aptitude install linux-headers-`uname -r` build-essential -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

It appears that CLVM is causing me some problems. Is there some way I can remove this software so I can continue installing VMware? 

Cheers,

Brent

---

### Post by leebrent on 2007-05-24
The following site fixed this error: 

[http://ubuntuforums.org/showthread.php?t=447459&highlight=clvm](http://ubuntuforums.org/showthread.php?t=447459&highlight=clvm)

---

