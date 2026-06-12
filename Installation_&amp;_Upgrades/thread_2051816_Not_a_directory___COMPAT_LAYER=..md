---
title: "Not a directory: __COMPAT_LAYER=."
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by kernelshell on 2012-09-02
sam@lym-Studio-1535:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up install-info (4.13a.dfsg.1-8ubuntu2) ...
Not a directory: __COMPAT_LAYER=.
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

sam@lym-Studio-1535:~$ sudo apt-get reinstall intall-info 
E: Invalid operation reinstall
sam@lym-Studio-1535:~$ sudo apt-get install install-info --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up install-info (4.13a.dfsg.1-8ubuntu2) ...
Not a directory: __COMPAT_LAYER=.
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

sam@lym-Studio-1535:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up install-info (4.13a.dfsg.1-8ubuntu2) ...
Not a directory: __COMPAT_LAYER=.
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

