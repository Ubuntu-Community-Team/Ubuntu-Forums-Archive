---
title: "Can't install openssh-server (among other things)"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by spintriae on 2008-06-30
Would somebody please explain this to me?

```
sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ssh-askpass rssh molly-guard
The following NEW packages will be installed:
  openssh-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/248kB of archives.
After unpacking 655kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 
dpkg: serious warning: files list file for package `laptop-detect' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xfce4-verve-plugin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gnupginterface' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `hal-info' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/openssh-server_1%3a4.6p1-5build1_i386.deb (--unpack):
 files list file for package `zlib1g' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-server_1%3a4.6p1-5build1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

