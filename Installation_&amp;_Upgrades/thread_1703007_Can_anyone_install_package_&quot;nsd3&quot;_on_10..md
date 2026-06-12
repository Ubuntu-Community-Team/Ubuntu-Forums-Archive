---
title: "Can anyone install package &quot;nsd3&quot; on 10.04.2?"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-03-08
Package **[FONT=Courier New]nsd3[/FONT]** looks like it is totally fubar.  It worked OK in 9.10.  But in 10.04.2 it gets really fouled up.  It won't finish the install because it needs /etc/nsd3/nsd.conf which it does not provide.  It does provide /etc/nsd3/nsd.conf.sample but that's not good enough.  Once the install is attempted, it won't finish, and it cannot be uninstalled.

I'd also like to know why tools like dpkg, aptitude and apt-get cannot uninstall a package that is only partially installed.  They should know what files are put in, and take them out.

Edit:  here is a log on a freshly booted LiveCD (thus very clean) system (sources.list updated to find the package):
```
root@ubuntu:~# time script -c 'apt-get --yes install nsd3' /tmp/nsd3.log
Script started, file is /tmp/nsd3.log
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nsd3
0 upgraded, 1 newly installed, 0 to remove and 252 not upgraded.
Need to get 898kB of archives.
After this operation, 1,729kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ lucid/universe nsd3 3.2.4-1 [898kB]
Fetched 898kB in 6s (130kB/s)                                                                                         
Selecting previously deselected package nsd3.
(Reading database ... 126677 files and directories currently installed.)
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
Errors were encountered while processing:
 nsd3
E: Sub-process /usr/bin/dpkg returned an error code (1)
Script done, file is /tmp/nsd3.log

real    0m8.955s
user    0m1.190s
sys     0m0.330s
root@ubuntu:~# 
```

---

