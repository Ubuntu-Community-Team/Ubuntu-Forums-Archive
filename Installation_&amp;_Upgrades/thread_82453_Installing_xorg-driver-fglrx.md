---
title: "Installing xorg-driver-fglrx"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by Kimppa on 2005-10-26
Hello

I'm trying to install ati drivers, but I'm having troubles installing xorg-driver-fglrx
This is the output

> 
root@kleppane:/home/kimppa # apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  nvidia-glx
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 1 to remove and 117 not upgraded.
Need to get 0B/8325kB of archives.
After unpacking 13,8MB of additional disk space will be used.
Do you want to continue [Y/n]?

Preconfiguring packages ...
(Reading database ... 139601 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/X11R6/lib/libGL.so.1' with
  different file `/usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa', not allowed
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@kleppane:/home/kimppa #


Any ideas how to fix this?

Thank you in advance

Kimppa

---

