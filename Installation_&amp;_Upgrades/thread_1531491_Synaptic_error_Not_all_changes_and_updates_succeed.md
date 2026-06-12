---
title: "Synaptic error: Not all changes and updates succeeded."
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by lunatico on 2010-07-15
Hello!

I installed 10.04 and did the upgrades. After that I installed a few programs.
Now when I try to install or uninstall something from synaptic it gives me this error at the end:
```
E: packagekit-backend-apt: subprocess installed post-installation script returned error exit status 2
```

I'm clueless as how to fix this. Can someone help me understand?

Thanks!

---

### Post by lunatico on 2010-07-15
Here is an example of running aptitude from command line:


```
~$ sudo aptitude install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  nmap 
The following partially installed packages will be configured:
  packagekit-backend-apt 
0 packages upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/1,589kB of archives. After unpacking 6,328kB will be used.
Writing extended state information... Done
Selecting previously deselected package nmap.
(Reading database ... 163073 files and directories currently installed.)
Unpacking nmap (from .../archives/nmap_5.00-3_i386.deb) ...
Processing triggers for man-db ...
Setting up packagekit-backend-apt (0.5.7-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing packagekit-backend-apt (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up nmap (5.00-3) ...

Errors were encountered while processing:
 packagekit-backend-apt
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

```

Thanks again!

---

