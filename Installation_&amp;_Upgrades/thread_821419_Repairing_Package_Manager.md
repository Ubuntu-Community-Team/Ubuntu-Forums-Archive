---
title: "Repairing Package Manager"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by 2hoosier on 2008-06-07
Synaptic has been returning error codes when updating packages, so I tried to reinstall it from the command line, with the following results:

 sudo apt-get install --reinstall synaptic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 110 not upgraded.
1 not fully installed or removed.
Need to get 1302kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main synaptic 0.61ubuntu9 [1302kB]
Fetched 1302kB in 1s (776kB/s)    
(Reading database ... 105807 files and directories currently installed.)
Preparing to replace synaptic 0.61ubuntu9 (using .../synaptic_0.61ubuntu9_i386.deb) ...
Unpacking replacement synaptic ...
Setting up synaptic (0.61ubuntu9) ...

Setting up update-manager (1:0.87.27) ...
file does not exist: /usr/lib/python2.5/site-packages/DistUpgrade/theme-switch-helper.py
file does not exist: /usr/lib/python2.5/site-packages/DistUpgrade/utils.py
pycentral: pycentral pkginstall: error byte-compiling files (32)
pycentral pkginstall: error byte-compiling files (32)
dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

What steps should I take to repair this?

---

### Post by dstew on 2008-06-07
> Synaptic has been returning error codes when updating packagesIf you are getting errors, re-installing is unlikely to solve the problem. What are the errors you get when you use Synaptic?

---

