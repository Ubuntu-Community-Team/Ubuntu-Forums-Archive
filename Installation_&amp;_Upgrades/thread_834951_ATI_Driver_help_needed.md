---
title: "ATI Driver help needed"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by melenor on 2008-06-20
all right recently i just tried to update the ATI driver by following this guide [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) before hardy following this site for the guides never produced problems, now i followed the guide but it came up with an error about libGL, and I was never able to fix the problem so i decided to try to just undo it but whenever i try to do anything about installing or removing i get this error, "E: xorg-driver-fglrx: subprocess post-removal script returned error exit status 2" I tried sudo apt-get install -f and i got this error
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 45.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 249681 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
  found `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

if i choose no then nothing happened and i still had the error.
I feel kinda stupid because the driver before hand worked with a few errors and i thought to just try the install to see if it fixed the problem. Thanks for your help
btw i have 64-bit ubuntu, but i didn't think that this belonged in the 64-bit forum because it didn't seem to have any error regrading 64-bit

---

