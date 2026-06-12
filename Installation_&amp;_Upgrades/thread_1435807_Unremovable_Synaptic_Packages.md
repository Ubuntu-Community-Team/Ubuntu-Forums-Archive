---
title: "Unremovable Synaptic Packages"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by dragonboss on 2010-03-21
I tried installing gnomenu and the pc froze mid-install when i rebooted i reinstalled gnomenu it didn't work and it left behind two dependencies when I try to remove them it gives this:
```

jeremy@Acer-lap-one:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up deskbar-applet (2.28.0-0ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing deskbar-applet (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-beagle (0.3.9-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-beagle (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 deskbar-applet
 python-beagle
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How do I fix this cos its annoying.

---

### Post by Chame_Wizard on 2010-03-22
Try```
sudo aptitude purge deb.package
```

---

### Post by dragonboss on 2010-03-22
Ok tried that and got this.

```
jeremy@Acer-lap-one:~$ sudo aptitude purge deskbar-applet
[sudo] password for jeremy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  deskbar-applet{p} 
The following partially installed packages will be configured:
  python-beagle 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 5,313kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 182921 files and directories currently installed.)
Removing deskbar-applet ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing deskbar-applet (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 deskbar-applet
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done

```

---

