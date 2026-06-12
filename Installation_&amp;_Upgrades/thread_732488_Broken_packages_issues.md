---
title: "Broken packages issues"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by el_rawyy on 2008-03-22
[SIZE="3"]When I use this command an error message at bottom of this text always appears to me , what is the problem and what is the solutions.

-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.17-12-generic libmyspell3c2 linux-headers-2.6.17-12
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu6) ...
 * Loading ACPI modules...                                               [ OK ]
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 kubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 kubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 kubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/SIZE]

---

### Post by PmDematagoda on 2008-03-23
Try executing:-
```
sudo dpkg --configure -a
```

---

