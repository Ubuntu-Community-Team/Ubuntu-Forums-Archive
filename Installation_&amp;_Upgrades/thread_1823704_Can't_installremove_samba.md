---
title: "Can't install/remove samba"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by wbuntu on 2011-08-12
```

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  samba
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
39 not fully installed or removed.
Need to get 0 B/7,416 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 310325 files and directories currently installed.)
Preparing to replace samba 2:3.5.8~dfsg-1ubuntu2.2 (using .../samba_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/smbd not found.
dpkg: warning: subprocess old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/smbd not found.
dpkg: error processing /var/cache/apt/archives/samba_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 100
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
invoke-rc.d: unknown initscript, /etc/init.d/smbd not found.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 /var/cache/apt/archives/samba_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by papibe on 2011-08-12
Try this:
```
$ sudo apt-get --purge remove samba
$ sudo apt-get autoremove
$ sudo apt-get autoclean

```
Then:
```
$ sudo apt-get update
$ sudo apt-get install samba
```
Hope it helps,
Regards.

---

### Post by wbuntu on 2011-08-14
```

$ sudo apt-get --purge remove samba
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
39 not fully installed or removed.
After this operation, 21.2 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing samba (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  samba
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
39 not fully installed or removed.
Need to get 0 B/7,416 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 310325 files and directories currently installed.)
Preparing to replace samba 2:3.5.8~dfsg-1ubuntu2.2 (using .../samba_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/smbd not found.
dpkg: warning: subprocess old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/smbd not found.
dpkg: error processing /var/cache/apt/archives/samba_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 100
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
invoke-rc.d: unknown initscript, /etc/init.d/smbd not found.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 /var/cache/apt/archives/samba_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
39 not fully installed or removed.
Need to get 0 B/7,416 kB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 310325 files and directories currently installed.)
Preparing to replace samba 2:3.5.8~dfsg-1ubuntu2.2 (using .../samba_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/smbd not found.
dpkg: warning: subprocess old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/smbd not found.
dpkg: error processing /var/cache/apt/archives/samba_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 100
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
invoke-rc.d: unknown initscript, /etc/init.d/smbd not found.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 /var/cache/apt/archives/samba_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dino99 on 2011-08-14
sudo rm /var/cache/apt/archives/*

then open nautilus and search for "samba" (selecting "system files" not /home), check the path (right click -> property) to delete each related samba file found (sudo rm ...) (folder is remove with sudo rm -rf ...)

then update

---

