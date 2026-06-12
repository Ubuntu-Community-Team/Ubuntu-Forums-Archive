---
title: "[SOLVED] Upgrading to Hardy - dpkg Errors"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by reg2117 on 2008-06-12
Forum Members,

I am attempting to upgrade to Kubuntu 8 and have received the following errors during installation:
```
~$ sudo apt-get install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-16-generic libnspr4 linux-headers-2.6.20-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                                                                         [ OK ]
 * Starting ACPI services...                                                                                              invoke-rc.d: initscript acpid, action "start" failed.
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

```

I have tried the following code suggested at [[COLOR="Blue"]this thread[/COLOR]]("http://http://ubuntuforums.org/showthread.php?t=825170").

```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

This produced the same error as above.

The next recommendation is to remove the programs causing an error.

[B]Can I remove and reinstall the following programs without too many hiccups?
[/B]     acpid
     acpi-support
     powermanagement-interface
     kubuntu-desktop

Is this the best method for completing the upgrade? Any advice would be much appreciated!

---

### Post by Partyboi2 on 2008-06-12
try
```
sudo /etc/init.d/acpid stop
sudo dpkg --configure acpid
sudo dpkg --configure -a

```

---

### Post by reg2117 on 2008-06-12
Brillant! This worked like a charm. The code completed the installation and I'm happily running 8.04.

---

