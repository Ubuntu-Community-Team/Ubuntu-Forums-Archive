---
title: "Update Samba on 12.04"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by dalewis62 on 2013-05-23
When I manually install software I get errors while system tries to apply updates to samba.  I have also tried to manually update samba with the following and included my error messages.  Does anyone have any ideas to work around or through this problem?

$ sudo apt-get --reinstall install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-37-generic linux-image-3.2.0-32-generic
  linux-image-3.2.0-38-generic linux-image-3.2.0-39-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cups
Suggested packages:
  printer-driver-hpcups hplip cups-pdf openbsd-inetd inet-superserver
  smbldap-tools ldb-tools ctdb
The following packages will be upgraded:
  cups samba
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
27 not fully installed or removed.
Need to get 0 B/9,345 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 430931 files and directories currently installed.)
Preparing to replace cups 1.5.3-0ubuntu6 (using .../cups_1.5.3-0ubuntu8_amd64.deb) ...
invoke-rc.d: initscript cups, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript cups, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/cups_1.5.3-0ubuntu8_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace samba 2:3.6.3-2ubuntu2.4 (using .../samba_2%3a3.6.3-2ubuntu2.6_amd64.deb) ...
invoke-rc.d: initscript nmbd, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript nmbd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/samba_2%3a3.6.3-2ubuntu2.6_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
invoke-rc.d: initscript smbd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/cups_1.5.3-0ubuntu8_amd64.deb
 /var/cache/apt/archives/samba_2%3a3.6.3-2ubuntu2.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

