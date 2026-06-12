---
title: "bzr installation problem -- launchpad"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by dascheer on 2010-01-24
Not sure where to turn to, noob here.  Tried to download and install bzr to test out gnome-activity-journal and zeitgeist, but got an error.  posted error to launchpad [HTML]https://bugs.launchpad.net/ubuntu/+source/bzrtools/+bug/509914[/HTML]

and was directed to workaround [HTML]https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096[/HTML]

Below is what the terminal printed out when i got to the second step.

```
user@laptop:/var/lib/dpkg/info$ sudo apt-get remove --purge bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-paramiko
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bzr* bzrtools*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 22.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 20%
dpkg: warning: files list file for package `bzr' missing, assuming package has no files currently installed.
(Reading database ... 90%
dpkg: warning: files list file for package `bzrtools' missing, assuming package has no files currently installed.
(Reading database ... 156538 files and directories currently installed.)
Removing bzrtools ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing bzrtools (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Removing bzr ...
pycentral: pycentral pkgremove: package bzr is not installed
pycentral pkgremove: package bzr is not installed
dpkg: error processing bzr (--purge):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 bzrtools
 bzr
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas?  Thanks!

---

