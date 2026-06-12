---
title: "error installing python-minimal on Ubuntu 18.04 LTS - wrong path in package index"
date: 2021-02-25
forum: Installation &amp; Upgrades
---

### Post by spfrfn on 2021-02-25
First time forum user. I'm not sure where to post this, but here goes.
On Ubuntu 18.04, I cannot install anything python2 related or any packages depending on it (for instance, etckeeper), because of an apparent error in the package index files 

[http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-amd64/](http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-amd64/)[Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-amd64/Packages.gz") 

contains the following definition:

Package: libpython2.7-minimal
Architecture: amd64
Version: 2.7.17-1~18.04ubuntu1.3
Multi-Arch: same
Priority: optional
Section: python
Source: python2.7
Origin: Ubuntu
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 2783
Recommends: libpython2.7-stdlib
Conflicts: binfmt-support (<< 1.1.2)
Breaks: python2.7-minimal (<< 2.7.4~rc1-1~)
Replaces: libpython2.7-stdlib (<< 2.7.8-7), python2.7 (<< 2.7.4-2), python2.7-minimal (<< 2.7.3-10)
Filename: pool/main/p/python2.7/libpython2.7-minimal_2.7.17-1~18.04ubuntu1.3_amd64.deb
....

But 
[http://archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7-minimal_2.7.17-1~18.04ubuntu1.3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7-minimal_2.7.17-1~18.04ubuntu1.3_amd64.deb)
does not exist. instead, there is a
[http://archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7-minimal_2.7.17-1~18.04ubuntu1.2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7-minimal_2.7.17-1~18.04ubuntu1.2_amd64.deb)

This results in the following:
root@somewhere:/home/someone# apt update
Hit:1 <snip>
Hit:2 <snip>
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]
Hit:4 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:5 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:6 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Fetched 88.7 kB in 1s (133 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.

root@somewhere:/home/someone# apt install etckeeper
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  libpython-stdlib libpython2.7-minimal libpython2.7-stdlib python python-minimal python2.7 python2.7-minimal
Suggested packages:
  python-doc python-tk python2.7-doc binutils binfmt-support
The following NEW packages will be installed:
  etckeeper libpython-stdlib libpython2.7-minimal libpython2.7-stdlib python python-minimal python2.7 python2.7-minimal
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3787 kB/3991 kB of archives.
After this operation, 17.0 MB of additional disk space will be used.
Do you want to continue? [Y/n]
Err:1 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libpython2.7-minimal amd64 2.7.17-1~18.04ubuntu1.3
  404  Not Found [IP: 141.30.62.26 80]
Err:2 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 python2.7-minimal amd64 2.7.17-1~18.04ubuntu1.3
  404  Not Found [IP: 141.30.62.26 80]
Err:3 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 libpython2.7-stdlib amd64 2.7.17-1~18.04ubuntu1.3
  404  Not Found [IP: 141.30.62.26 80]
Err:4 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 python2.7 amd64 2.7.17-1~18.04ubuntu1.3
  404  Not Found [IP: 141.30.62.26 80]
E: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7-minimal_2.7.17-1~18.04ubuntu1.3_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7-minimal_2.7.17-1~18.04ubuntu1.3_amd64.deb)  404  Not Found [IP: 141.30.62.26 80]
E: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7-minimal_2.7.17-1~18.04ubuntu1.3_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7-minimal_2.7.17-1~18.04ubuntu1.3_amd64.deb)  404  Not Found [IP: 141.30.62.26 80]
E: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7-stdlib_2.7.17-1~18.04ubuntu1.3_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7-stdlib_2.7.17-1~18.04ubuntu1.3_amd64.deb)  404  Not Found [IP: 141.30.62.26 80]
E: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7_2.7.17-1~18.04ubuntu1.3_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7_2.7.17-1~18.04ubuntu1.3_amd64.deb)  404  Not Found [IP: 141.30.62.26 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by spfrfn on 2021-02-25
Correction: As of now, i can only find this error on [URL="http://de.archive.ubuntu.com/ubuntu"]http://de.archive.ubuntu.com
[/URL]anymore. It appears to not be the case or have been fixed on [http://archive.ubuntu.com](http://archive.ubuntu.com) , so i can work around it by changing my /etc/apt/sources.list to that for now.

---

