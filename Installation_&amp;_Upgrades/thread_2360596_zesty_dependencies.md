---
title: "zesty dependencies"
date: 2017-05-06
forum: Installation &amp; Upgrades
---

### Post by zkab on 2017-05-06
I have installed Xubuntu 17.04 zesty (64 bits) from scratch.
When installing Corel AfterShot Pro I get following errors ...

```
loke@loke:~$ sudo dpkg -i Downloads/AfterShotPro3.deb 
Selecting previously unselected package aftershot3x64.
(Reading database ... 190543 files and directories currently installed.)
Preparing to unpack Downloads/AfterShotPro3.deb ...
Unpacking aftershot3x64 (330234:3.3.0.234) ...
dpkg: dependency problems prevent configuration of aftershot3x64:
 aftershot3x64 depends on libpng12-0; however:
  Package libpng12-0 is not installed.
 aftershot3x64 depends on libgstreamer0.10-0; however:
  Package libgstreamer0.10-0 is not installed.
 aftershot3x64 depends on libgstreamer-plugins-base0.10-0; however:
  Package libgstreamer-plugins-base0.10-0 is not installed.

dpkg: error processing package aftershot3x64 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info (1.8-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Errors were encountered while processing:
 aftershot3x64
loke@loke:~$ dpkg -l after*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version             Architecture        Description
+++-=============================-===================-===================-===============================================================
iU  aftershot3x64                 330234:3.3.0.234    amd64               Corel AfterShot 3 (64-bit)

```

I tried to install the dependencies but it complains ...

```
loke@loke:~$ sudo apt install libpng12-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libpng12-0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libpng12-0' has no installation candidate
loke@loke:~$ 
loke@loke:~$ sudo apt install libgstreamer0.10-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgstreamer0.10-0
E: Couldn't find any package by glob 'libgstreamer0.10-0'
E: Couldn't find any package by regex 'libgstreamer0.10-0'
loke@loke:~$ sudo apt install libgstreamer-plugins-base0.10-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgstreamer-plugins-base0.10-0
E: Couldn't find any package by glob 'libgstreamer-plugins-base0.10-0'
E: Couldn't find any package by regex 'libgstreamer-plugins-base0.10-0'
loke@loke:~$ 

```

How can it be fixed ?

---

### Post by howefield on 2017-05-06
From the Corel website : [https://support.corel.com/hc/en-us/articles/235552727-AfterShot-Pro-Installation-fails-on-Ubuntu-16-10](https://support.corel.com/hc/en-us/articles/235552727-AfterShot-Pro-Installation-fails-on-Ubuntu-16-10)

There will be a reason why the package above only seem to appear in the LTS versions of Ubuntu but I'm not sure what that might be and usually wouldn't recommend mixing packages from different Ubuntu versions, but the choice is yours ;)

---

### Post by zkab on 2017-05-06
OK - thanks ... I agree with you that mixing packages from different Ubuntu versions is not a good idea.
I will ask Corel support why zesty isn't supported ...

---

