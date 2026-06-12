---
title: "clamav installtion"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by soongwoo on 2006-02-18
I'm new to Ubuntu and using 5.10.
When I install clamav, I encounter an error as followings:
I enable Universe, Multiverse and Backport.
I could not find proper articles in Ubuntu form regarding Clamav installation.

Is there a way to resolve this problem?
Or suggest another antivirus program.

Thanks
soongwoo

```
$ sudo apt-get install clamav clamav-daemon clamav-freshclam
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  clamav-base libclamav1 libgmp3c2 libgmpxx3
Suggested packages:
  clamav-docs daemon
The following NEW packages will be installed:
  clamav clamav-base clamav-daemon clamav-freshclam libclamav1 libgmp3c2 libgmpxx3
0 upgraded, 7 newly installed, 0 to remove and 63 not upgraded.
Need to get 3784kB of archives.
After unpacking 5071kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://kr.archive.ubuntu.com breezy/main libgmpxx3 4.1.4-10ubuntu1 [171kB]
Get:2 http://kr.archive.ubuntu.com breezy/main libgmp3c2 4.1.4-10ubuntu1 [314kB]
Get:3 http://kr.archive.ubuntu.com breezy-backports/universe libclamav1 0.87.1-1~breezy1 [257kB]
Get:4 http://kr.archive.ubuntu.com breezy-backports/universe clamav-base 0.87.1-1~breezy1 [169kB]
Get:5 http://kr.archive.ubuntu.com breezy-backports/universe clamav-freshclam 0.87.1-1~breezy1 [2771kB]
Get:6 http://kr.archive.ubuntu.com breezy-backports/universe clamav 0.87.1-1~breezy1 [64.8kB]
Get:7 http://kr.archive.ubuntu.com breezy-backports/universe clamav-daemon 0.87.1-1~breezy1 [37.8kB]
Fetched 3784kB in 19s (192kB/s)

Preconfiguring packages ...
Selecting previously deselected package libgmpxx3.
(Reading database ... 57339 files and directories currently installed.)
Unpacking libgmpxx3 (from .../libgmpxx3_4.1.4-10ubuntu1_i386.deb) ...
Selecting previously deselected package libgmp3c2.
Unpacking libgmp3c2 (from .../libgmp3c2_4.1.4-10ubuntu1_i386.deb) ...
Selecting previously deselected package libclamav1.
Unpacking libclamav1 (from .../libclamav1_0.87.1-1~breezy1_i386.deb) ...
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.87.1-1~breezy1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.87.1-1~breezy1_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.87.1-1~breezy1_i386.deb) ...
Selecting previously deselected package clamav-daemon.
Unpacking clamav-daemon (from .../clamav-daemon_0.87.1-1~breezy1_i386.deb) ...
Setting up clamav-base (0.87.1-1~breezy1) ...
Adding system user `clamav'...
Adding new group `clamav' (114).
Adding new user `clamav' (114) with group `clamav'.
Not creating home directory.
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (= 0.87.1-1~breezy1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-base (= 0.87.1-1~breezy1); however:
  Package clamav-base is not configured yet.
 clamav-daemon depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav-daemon (--configure):
 dependency problems - leaving unconfigured
Setting up libgmpxx3 (4.1.4-10ubuntu1) ...

Setting up libgmp3c2 (4.1.4-10ubuntu1) ...

Setting up libclamav1 (0.87.1-1~breezy1) ...

Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
 clamav-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by rfruth on 2006-02-18
clamAG is a very good choice but you may have to RTFM [https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29]("https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29")

---

### Post by soongwoo on 2006-02-18
Thank rfruth very much.

But, what the error messages mean?
Is clamav package installed without problem?

soongwoo

---

