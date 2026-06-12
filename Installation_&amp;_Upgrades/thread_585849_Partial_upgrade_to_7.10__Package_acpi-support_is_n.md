---
title: "Partial upgrade to 7.10:  Package acpi-support is not configured yet"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by stephanecharette on 2007-10-21
I'm trying to upgrade one of my (virtual) machines from 7.04 to 7.10.  Something somewhere went wrong, and the upgrade process didn't finish.  Now it keeps finding the same packages that need to be upgraded, but it always dies.  When I run it from the command line, this is what I get -- can anyone help?

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    
invoke-rc.d: initscript acpid, action "start" failed.
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
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 ubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pumalite on 2007-10-21
Try sudo dpkg --configure -a

---

### Post by jcs79 on 2007-10-22
I fixed this by doing the following:

1. Used aptitude (or synaptic if you like) and marked acpid for COMPLETE removal. This removes the config files as well.
2. This also made me remove the packages ubuntu-desktop, powermanagement-interface, and acpi-support. I was okay with it.
3. After removal, went back in and manually selected each of these package for installation. The install completed successfully.
4.:guitar:

---

