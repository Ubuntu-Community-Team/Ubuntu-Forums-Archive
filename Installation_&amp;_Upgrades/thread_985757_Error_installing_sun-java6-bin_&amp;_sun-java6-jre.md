---
title: "Error installing sun-java6-bin &amp; sun-java6-jre"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by sugardewie on 2008-11-17
I am new to Ubuntu.

See error below.

root@server1:/# apt-get install sun-java6-bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  sun-java6-jre
Suggested packages:
  binfmt-support sun-java6-fonts sun-java6-plugin ia32-sun-java6-plugin
  ttf-baekmuk ttf-unfonts ttf-unfonts-core ttf-kochi-gothic
  ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho ttf-wqy-zenhei
The following NEW packages will be installed:
  sun-java6-bin sun-java6-jre
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 33.6MB of archives.
After this operation, 96.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse sun-java6-bin 6-06-0ubuntu1 [2.3MB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse sun-java6-jre 6-06-0ubuntu1 [634kB]
Fetched 33.6MB in 33s (999kB/s)
Preconfiguring packages ...
Selecting previously deselected package sun-java6-bin.
(Reading database ... 11784 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-06-0ubuntu1_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-06-0ubuntu1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Setting up sun-java6-bin (6-06-0ubuntu1) ...
/proc is not mounted; some java apps may fail
Aborted
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 134
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-06-0ubuntu1) | ia32-sun-java6-bin = 6-06-0ubuntu1); however:
  Package sun-java6-bin is not configured yet.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin
 sun-java6-jre
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks,
Dewie

---

### Post by inobe on 2008-11-17
hi, have you installed restricted extras ?

it includes java, flash and various other apps and codecs !

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by melmantheman on 2011-07-18
that does not work for me either even with the restricted extras. it still poops out with the bin.

---

