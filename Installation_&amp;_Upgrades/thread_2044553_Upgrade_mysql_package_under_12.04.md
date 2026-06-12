---
title: "Upgrade mysql package under 12.04"
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by kamelie1706 on 2012-08-19
Hello,

When upgrade my packages with 
```
sudo apt-get upgrade
```I get

```
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
       Processing triggers for libreoffice-common ...
Setting up libreoffice-emailmerge (1:3.5.4-0ubuntu1.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic-pae
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Rest of packages seem to upgrade fine.

I have the propblem since I upgarde to ubuntu 12.04.

Thanks

---

