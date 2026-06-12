---
title: "Cluster LVM Daemon problem"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by Slevin on 2006-10-07
When I try to install/uninstall any program with apt becomes this problem:
slevin@Sk8rafleXX:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

When I try to remove clvm an error happens again:
slevin@Sk8rafleXX:~$ dpkg -P clvm
dpkg: requested operation requires superuser privilege
slevin@Sk8rafleXX:~$ sudo dpkg -P clvm
(Reading database ... 134787 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--purge):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm

slevin@Sk8rafleXX:~$ sudo apt-get remove clvm
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  clvm
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 487kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 134787 files and directories currently installed.)
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
slevin@Sk8rafleXX:~$

how can I fix it?

---

### Post by siucdude on 2007-01-05
any upddates on this,??

---

### Post by ashahab on 2007-02-12
sudo rm /etc/init.d/clvm
and then
sudo apt-get remove clvm

---

