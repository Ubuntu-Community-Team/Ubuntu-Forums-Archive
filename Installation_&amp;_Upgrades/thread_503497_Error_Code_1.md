---
title: "Error Code 1"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by rsvasan72 on 2007-07-18
Hi,
I was trying to uninstall a wrong scanner driver using Synaptic Package Manager, I get the following Error message "Returned Error code 1" I am copying the entire command and response I got here

> :~$ sudo aptitude remove brscan2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  brscan2 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 140076 files and directories currently installed.)
Removing brscan2 ...
/bin/sh: Can't open exit 0
dpkg: error processing brscan2 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 brscan2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Any help to resolve this issue would be appreciated.
Thanks much
Srini

---

