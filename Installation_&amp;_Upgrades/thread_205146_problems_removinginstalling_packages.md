---
title: "problems removing/installing packages"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by rold50 on 2006-06-28
I'm trying to resolve this problem.. I don't know why I keep getting this error
upgrade manager wanted to upgrade ubuntu desktop then I got an error about glib. so I tried apt-get remove... etc.. apt-get --reinstall install.. 
everytime it gives me the glibc error message.

Is there a way to remove this package? 

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  ubuntu-docs
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 37.2MB will be freed.
Writing extended state information... Done
(Reading database ... 130731 files and directories currently installed.)
Removing ubuntu-docs ...
*** glibc detected *** double free or corruption (!prev): 0x08272608 ***
/var/lib/dpkg/info/ubuntu-docs.postrm: line 6:  5482 Aborted                 scrollkeeper-update -q
dpkg: error processing ubuntu-docs (--remove):
 subprocess post-removal script returned error exit status 134
Errors were encountered while processing:
 ubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

