---
title: "Update problem (circular dependency?)"
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by sailingbye on 2011-11-02
Hi

I have a problem that is preventing me from installing, updating or removing packages and hence from upgrading from Ubuntu 10.04.

The package  education-astronomy  is marked for removal but removal fails due to a dpkg error caused by a missing file. It appears that the missing file (/usr/share/cdd/cdd-utils) comes from the  cdd-common  package. However, it appears that the installation of  cdd-common  depends upon the removal of  education-astronomy.

Some of the commands I've tried, and their output, are detailed below.

Can anyone help?

Detail
------

Command:

apt-get install -f

Output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  education-tasks
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  education-astronomy
0 upgraded, 0 newly installed, 1 to remove and 214 not upgraded.
1 not fully installed or removed.
After this operation, 65.5kB disk space will be freed.
Do you want to continue [Y/n]? Y          
(Reading database ... 368376 files and directories currently installed.)
Removing education-astronomy ...
/etc/cdd/cdd.conf: line 14: /usr/share/cdd/cdd-utils: No such file or directory
dpkg: error processing education-astronomy (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 education-astronomy
E: Sub-process /usr/bin/dpkg returned an error code (1)

Command:

sudo apt-get install cdd-common

Output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  education-tasks
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  education-astronomy
The following NEW packages will be installed
  cdd-common
0 upgraded, 1 newly installed, 1 to remove and 214 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,236B of archives.
After this operation, 24.6kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 368376 files and directories currently installed.)
Removing education-astronomy ...
/etc/cdd/cdd.conf: line 14: /usr/share/cdd/cdd-utils: No such file or directory
dpkg: error processing education-astronomy (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 education-astronomy
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sailingbye on 2011-11-02
I've made some progress since my original post, by downloading the package, unpacking it and putting the missing file(s) in place manually.

Before I mark this thread as solved, can anyone explain what might have caused this situation in the first place?

Thanks

---

