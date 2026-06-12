---
title: "Synaptic Package manager"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by owen_cook on 2008-05-10
Attempting to start Synaptic after a 60+meg upgrade

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so I run dpkg --configure -a

root@owen-desktop:~# dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 11 package `xserver-xorg-input-vmmouse':
 file details field `Size' not allowed in status file
root@owen-desktop:~# 

So the first 19 lines reads, line 11 is the size line. 

Every entry has the Size field.

=========================================================
Priority: optional
Section: x11
Installed-Size: 92
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1:12.4.3-1ubuntu1
Replaces: xserver-xorg (<< 6.8.2-35)
Provides: xserver-xorg-input-2
Depends: libc6 (>= 2.7-1), xserver-xorg-core (>= 2:1.4)
Size: 14676
Description: X.Org X server -- VMMouse input driver to use with VMWare
 This package provides the driver for the X11 vmmouse input device.
 .
 The VMMouse driver enables support for the special VMMouse protocol
 that is provided by VMware virtual machines to give absolute pointer
 positioning.
 .
 The vmmouse driver is capable of falling back to the standard "mouse"

=========================================================

Only one entry in Google, 2006 and not relevant to this problem

I am not sure if
   E: _cache->open() failed, please report.
is subsequent to the 'Size' problem

Are their any suggestions as how to correct this problem. I am tempted to back up all 0000 -0007 and remove the Size line in them all, but there maybe some other option


TIA


Owen

---

### Post by zvacet on 2008-05-10
```
sudo dpkg --configure -a
```

---

### Post by owen_cook on 2008-05-10
OK, removed all the Size: lines and now have this error, bit further down this time.



dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 19567 package `blt':
 `Depends' field, syntax error after reference to package `libx11-6udevmonitor'


Package: blt
Priority: optional
Section: libs
Installed-Size: 2708
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 2.4z-4ubuntu1
Replaces: blt-common, blt-demo (<< 2.4i-1), blt-dev (<< 2.4z-3), blt4.2, blt8.0, blt8.0-unoff
Provides: blt-common
Depends: libc6 (>= 2.7-1), libx11-6udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent


so I remove the "will print the received events for:" and then subsequent runs of sudo dpkg --configure -a start telling me colons are required after UDEV, the UEVENT and I am not sure of the structure of the file, yet

Interestinly a second Hardy installation I have on another partition does not have any files in /var/lib/dpkg/updates, presumeably becase I have done no updates on it.

Will keep going before I re install


Owen

---

### Post by owen_cook on 2008-05-10
End of story, 8 or 9 files in  /var/lib/dkpg were corrupted. Goodness knows how.

Removed all the corrupted packages and synaptic worked but told me I had 69 broken packages.

To fix would have cost 450 megs of download.


Simpler to reinstall


What fun


Thank you for your attention 


Owen

---

### Post by owen_cook on 2008-05-10
Just to wrap this up, started my 7.04 this morning and advised about a stack of updates, looked very similiar to the ones that 8.04 wanted.

However my second installation of 8.04 has not indicated that any updates are ready/available.

Also note that I am not the onlt one with this problem.

maybe its a build problem.

Will stick with the 7.04 for the time being

---

