---
title: "Possibly corrupt deb for libcairo1"
date: 2005-06-12
forum: Installation &amp; Upgrades
---

### Post by Tyr_7BE on 2005-06-12
I'm trying to install libcairo1 and here's what I keep getting:

[conor@conor-lt:~]$ sudo apt-get install libcairo1
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libpixman1
The following NEW packages will be installed:
  libcairo1 libpixman1
0 upgraded, 2 newly installed, 0 to remove and 21 not upgraded.
Need to get 172kB of archives.
After unpacking 438kB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main libpixman1 0.1.3-1 [50.7kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main libcairo1 0.3.0-1 [121kB]
Fetched 172kB in 0s (178kB/s)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

When I wget the actual deb file, dpkg returns an error:

[conor@conor-lt:~]$ sudo dpkg -i libcairo1_0.3.0-1_i386.deb
dpkg-deb: `libcairo1_0.3.0-1_i386.deb' is not a debian format archive
dpkg: error processing libcairo1_0.3.0-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 libcairo1_0.3.0-1_i386.deb


I get the same problems when I get libcairo1 from [http://packages.ubuntu.com](http://packages.ubuntu.com) as well...no matter where I download from, it's the same situation.

Is libcairo1 corrupt?  If not, what might be going wrong?  If so, to whom should I report this?

---

### Post by Tyr_7BE on 2005-06-13
Is nobody else getting this problem?  What happens when people try to do an "apt-get install --reinstall libcairo1"?

---

### Post by Tyr_7BE on 2005-06-13
I got it to work using the deb from [http://ftp.cs.umn.edu/pub/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)

---

