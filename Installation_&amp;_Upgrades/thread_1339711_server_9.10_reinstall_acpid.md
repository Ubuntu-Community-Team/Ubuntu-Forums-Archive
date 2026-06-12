---
title: "server 9.10 reinstall acpid"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by lbharti on 2009-11-27
I tried to reinstall acpid, but it has brought me down to the following state:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  toshset ethtool xinput finger laptop-mode-tools
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acpi-support acpid
0 upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 643kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 56285 files and directories currently installed.)
Removing acpi-support ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing acpi-support (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Removing acpid ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing acpid (--remove):
 subprocess installed pre-removal script returned error exit status 2
Errors were encountered while processing:
 acpi-support
 acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
It would not remove, nor reinstall the packages. What should I do?

---

