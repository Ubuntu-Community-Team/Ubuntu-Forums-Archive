---
title: "NFS install fails with various errors"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by nexist on 2008-08-05
I have an Ubuntu Server running 8.04. Having issues with connecting to Samba, I decided to try and install NFS.

```
nexist@obelisk:~$ sudo apt-get install nfs-kernel-server
[sudo] password for nexist: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libevent1 libgssglue1 libnfsidmap2 librpcsecgss3 nfs-common portmap
The following NEW packages will be installed:
  libevent1 libgssglue1 libnfsidmap2 librpcsecgss3 nfs-common
  nfs-kernel-server portmap
0 upgraded, 7 newly installed, 0 to remove and 22 not upgraded.
Need to get 0B/493kB of archives.
After this operation, 1495kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 
dpkg: serious warning: files list file for package `samba-doc' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ifupdown' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/libevent1_1.3e-1_i386.deb (--unpack):
 files list file for package `libslp1' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libevent1_1.3e-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have cleaned and removed and -f & -a again and again to no avail. Does anyone have any other ideas?

---

