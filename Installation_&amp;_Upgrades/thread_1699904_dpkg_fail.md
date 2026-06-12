---
title: "dpkg fail"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-03-04
What is the RIGHT WAY to completely and totally remove a package that isn't installed correctly?

```
feynman/root/x0 /root 22# dpkg --force-all --purge nsd3
(Reading database ... 110799 files and directories currently installed.)
Removing nsd3 ...
Could not open /etc/nsd3/nsd.conf: No such file or directory
 * Stopping nsd3...
Could not open /etc/nsd3/nsd.conf: No such file or directory
invoke-rc.d: initscript nsd3, action "stop" failed.
dpkg: error processing nsd3 (--purge):
 subprocess installed pre-removal script returned error exit status 1
Could not open /etc/nsd3/nsd.conf: No such file or directory
Could not open /etc/nsd3/nsd.conf: No such file or directory
 * Building nsd3 zones...
Could not open /etc/nsd3/nsd.conf: No such file or directory
invoke-rc.d: initscript nsd3, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nsd3
feynman/root/x0 /root 23# 
```

---

### Post by Skaperen on 2011-03-04
Here's more info.  It looks like the nsd3 package is broken and causes the package system to break as a result.  This is on 10.04.2 LTS.

```
maxwell/root/x0 /root 4# logcmd -s apt-get-install-nsd3 apt-get install nsd3
Script started, file is /tmp/20110304-122104-002148-apt-get-install-nsd3.log
12:21:04 [2154] EXECUTING: 'apt-get' 'install' 'nsd3'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nsd3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 898kB of archives.
After this operation, 1,729kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe nsd3 3.2.4-1 [898kB]
Fetched 898kB in 2s (376kB/s)
Selecting previously deselected package nsd3.
(Reading database ... 45406 files and directories currently installed.)
Unpacking nsd3 (from .../nsd3_3.2.4-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up nsd3 (3.2.4-1) ...
dpkg-statoverrides: warning: --update given but /etc/nsd3/nsd.conf does not exist
Could not open /etc/nsd3/nsd.conf: No such file or directory
Could not open /etc/nsd3/nsd.conf: No such file or directory
 * Building nsd3 zones...
Could not open /etc/nsd3/nsd.conf: No such file or directory
invoke-rc.d: initscript nsd3, action "start" failed.
dpkg: error processing nsd3 (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
[[ 0m3s real 3.621 - user 0.920 - sys 0.200 - 30.92% ]]
12:21:07 [2154] FINISHED - status = 100
Script done, file is /tmp/20110304-122104-002148-apt-get-install-nsd3.log
maxwell/root/x0 /root 5# 
```

---

### Post by zereshk on 2011-08-15
This happened for me too:

```
root@server:/etc# apt-get --purge remove nsd3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  nsd3*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,786kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 29612 files and directories currently installed.)
Removing nsd3 ...
 * Stopping nsd3...                                                             invoke-rc.d: initscript nsd3, action "stop" failed.
dpkg: error processing nsd3 (--purge):
 subprocess installed pre-removal script returned error exit status 1
 * Starting nsd3...                                                      [ OK ] 
Errors were encountered while processing:
 nsd3
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Frogs Hair on 2011-08-15
I don't know if it would make a difference , but you could try from the synaptic package manager . Then remove the residual configuration if any .

---

