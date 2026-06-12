---
title: "Xubuntu 7.10 Errors"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by Sammm_ on 2007-10-08
I installed Xubuntu 7.10, through "update-manager -d". I thought it all went find and left it, but I ran i today and it's giving these errors when I try to use apt-get and what not...

```
Setting up acpid (1.0.4-5ubuntu8) ...
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
dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 xubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 xubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up ssmtp (2.61-12ubuntu1) ...
export: 44: #: bad variable name
dpkg: error processing ssmtp (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 xubuntu-desktop
 ssmtp
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas how to fix this? Cheers.

---

