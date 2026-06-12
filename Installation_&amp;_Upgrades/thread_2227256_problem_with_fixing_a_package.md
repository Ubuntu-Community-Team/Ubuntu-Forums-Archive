---
title: "problem with fixing a package"
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by hgabe on 2014-05-31
> 
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libjbig0
The following packages will be upgraded:
  libjbig0
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0 B/26.1 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Selecting previously unselected package libjbig0:amd64.
(Reading database ... 317083 files and directories currently installed.)
Preparing to unpack .../libjbig0_2.0-2ubuntu4.1_amd64.deb ...
Unpacking libjbig0:amd64 (2.0-2ubuntu4.1) over (2.0-2ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libjbig0_2.0-2ubuntu4.1_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libjbig0/changelog.Debian.gz', which is different from other instances of package libjbig0:amd64
Errors were encountered while processing:
 /var/cache/apt/archives/libjbig0_2.0-2ubuntu4.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


this after I tried installing codelite using these instructions
[http://www.sysads.co.uk/2014/05/install-codelite-5-4-ubuntu-debian-linux-mint/](http://www.sysads.co.uk/2014/05/install-codelite-5-4-ubuntu-debian-linux-mint/)

---

### Post by oldos2er on 2014-06-01
Why not install it from the Software Center?

---

### Post by Scott_Zhou on 2015-01-16
Hi, 

I had done the same thing with you and met the same problem. Had you fixed it?
I tried search but did not found a solution.
Do you have solution now?

Thanks!
Scott

---

