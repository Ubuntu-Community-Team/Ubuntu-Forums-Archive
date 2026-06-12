---
title: "Acpid Problems"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by nick_geetar on 2010-04-04
Alright I didn't want to post anything on this because I've seen many solutions for the same thing but none of them have worked. This is the output when ever i try to install anything. 



sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.6-9ubuntu4.9.04.3) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 acpid
 acpi-support
 ubuntu-desktop

---

