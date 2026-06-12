---
title: "cannot install libgtop2-10:i386"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by czsergey on 2014-12-08
[SIZE=2][FONT=arial]I need to install libgtop2-10:i386 package on 64bit system (Utopic). But dependencies cannot be met:

```
$ sudo apt-get install libgtop2-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libgtop2-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,540 B of archives.
After this operation, 90.1 kB of additional disk space will be used.
Get:1 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) utopic/main libgtop2-common all 2.30.0.is.2.30.0-0ubuntu1 [9,540 B]
Fetched 9,540 B in 0s (37.1 kB/s)    
Selecting previously unselected package libgtop2-common.
(Reading database ... 191592 files and directories currently installed.)
Preparing to unpack .../libgtop2-common_2.30.0.is.2.30.0-0ubuntu1_all.deb ...
Unpacking libgtop2-common (2.30.0.is.2.30.0-0ubuntu1) ...

$ sudo apt-get install libgtop2-10:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgtop2-10:i386 : Depends: libgtop2-common:i386 (>= 2.30.0.is.2.30.0-0ubuntu1) but it is not installable
E: Unable to correct problems, you have held broken packages.

$ sudo apt-get install libgtop2-common:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgtop2-common:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libgtop2-common:i386' has no installation candidate
```

So there is no libgtop2-common:i386 but there is libgtop2-common (all platforms) package and libgtop2-10:i386 depends on libgtop2-common:i386 and not libgtop2-common(:all). Is there a workaround for this or do I need to wait for fix of this ?[/FONT][/SIZE]

---

