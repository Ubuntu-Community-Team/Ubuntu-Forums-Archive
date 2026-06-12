---
title: "Can't remove  an app: error code 3 for DPKG"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by vargadanis on 2007-05-19
Hi!

I accidentally installed clvm and it also installed some other dependencies such as redhat-cluster-management or something similar. When trying to remove it I get an error message:
> dani@dani-laptop:~$ sudo aptitude remove clvm
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  app-install-data-commercial apport apport-gtk capplets-data 
  gnome-control-center gnome-panel gnome-panel-data 
  libgnome-window-settings1 libmetacity0 libpanel-applet2-0 libslab0 
  libsmbclient metacity metacity-common python-apport python-problem-report 
  rdesktop samba-common smbclient tzdata update-manager update-manager-core 
The following packages will be REMOVED:
  clvm 
0 packages upgraded, 0 newly installed, 1 to remove and 22 not upgraded.
Need to get 0B of archives. After unpacking 492kB will be freed.
Writing extended state information... Done
(Reading database ... 94043 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dani@dani-laptop:~$ 


The syslog:
> May 19 20:02:02 dani-laptop ccsd[4032]: Unable to connect to cluster infrastructure after 120 seconds. 
May 19 20:02:33 dani-laptop ccsd[4032]: Unable to connect to cluster infrastructure after 150 seconds. 
May 19 20:03:02 dani-laptop ccsd[4032]: Unable to connect to cluster infrastructure after 180 seconds. 
May 19 20:03:32 dani-laptop ccsd[4032]: Unable to connect to cluster infrastructure after 210 seconds. 
May 19 20:04:02 dani-laptop ccsd[4032]: Unable to connect to cluster infrastructure after 240 seconds. 
May 19 20:04:32 dani-laptop ccsd[4032]: Unable to connect to cluster infrastructure after 270 seconds. 
May 19 20:04:46 dani-laptop clvmd: Can't open cluster manager socket: No such file or directory
May 19 20:05:02 dani-laptop ccsd[4032]: Unable to connect to cluster infrastructure after 300 seconds. 


I tried dpkg-reconfigure but it also didn't work at all. How could I remove it than? I need to install some other softwares but aptitude or DPKG or apt-get doesn't let me as long as I have a broken package. Pls help!

Thx...

---

### Post by vargadanis on 2007-05-20
Nobody can help me?

---

### Post by vedace on 2007-05-20
This might be utterly useless, but try running synaptic, go to "edit" and click on "fix broken packages."  If that doesn't work, try
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by vargadanis on 2007-05-20
Nope... It didn't work... Any other suggestions?

---

### Post by leebrent on 2007-05-24
[http://ubuntuforums.org/showthread.php?t=447459&highlight=clvm](http://ubuntuforums.org/showthread.php?t=447459&highlight=clvm) worked for me. I had the same problems

---

