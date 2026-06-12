---
title: "Apt-Get Install Errors"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by ndube on 2006-12-19
I am running edgy ( 6.10 ). I just tried to install k3d and the install failed with the following errors

ndube@JPTI-NETTECH-LX:~$ sudo apt-get install k3d
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
k3d is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up k3d (0.5.12.0-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of k3d-dev:
 k3d-dev depends on k3d (= 0.5.12.0-1ubuntu2); however:
  Package k3d is not configured yet.
dpkg: error processing k3d-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 k3d
 k3d-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now every time I run apt-get it fails because it is trying to finish k3d and k3d-dev. Does anyone know how to fix this? I tried doing a complete remove via synaptic and apt-get remove and both fail.

---

### Post by jrib on 2006-12-19
> **ndube said:**
> I am running edgy ( 6.10 ). I just tried to install k3d and the install failed with the following errors

ndube@JPTI-NETTECH-LX:~$ sudo apt-get install k3d
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
k3d is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up k3d (0.5.12.0-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of k3d-dev:
 k3d-dev depends on k3d (= 0.5.12.0-1ubuntu2); however:
  Package k3d is not configured yet.
dpkg: error processing k3d-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 k3d
 k3d-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now every time I run apt-get it fails because it is trying to finish k3d and k3d-dev. Does anyone know how to fix this? I tried doing a complete remove via synaptic and apt-get remove and both fail.

this is [https://bugs.launchpad.net/distros/ubuntu/+source/k3d/+bug/64848](https://bugs.launchpad.net/distros/ubuntu/+source/k3d/+bug/64848)

If you edit /var/lib/dpkg/status yourself and correct the typo, you should be able to fix the problem.  Make a backup of this file before editing.

---

### Post by ndube on 2006-12-19
Thanks alot _jason. Fixed in less that 1 minute. At least the bug is fixed in feisty...

---

