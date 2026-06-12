---
title: "apt problem with libpam-modules"
date: 2021-01-22
forum: Installation &amp; Upgrades
---

### Post by awers2 on 2021-01-22
Hi

I would need help. Why does apt have a problem with sed in the etc directory (sed: cannot rename /etc/sedlVbCpt: Device or resource busy)? I have 950M of free space /. System is ubuntu touch 16.04

> [LEFT]apt-get install libpam-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libpam-modules-bin
Recommended packages:
  update-motd
The following packages will be upgraded:
  libpam-modules libpam-modules-bin
2 upgraded, 0 newly installed, 0 to remove and 389 not upgraded.
Need to get 255 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main arm64 libpam-modules-bin arm64 1.1.8-3.2ubuntu2.3 [33.2 kB]
Get:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main arm64 libpam-modules arm64 1.1.8-3.2ubuntu2.3 [222 kB]
Fetched 255 kB in 0s (544 kB/s)         
Preconfiguring packages ...
(Reading database ... 50978 files and directories currently installed.)
Preparing to unpack .../libpam-modules-bin_1.1.8-3.2ubuntu2.3_arm64.deb ...
Unpacking libpam-modules-bin (1.1.8-3.2ubuntu2.3) over (1.1.8-3.2ubuntu2.1) ...
Setting up libpam-modules-bin (1.1.8-3.2ubuntu2.3) ...
(Reading database ... 50978 files and directories currently installed.)
Preparing to unpack .../libpam-modules_1.1.8-3.2ubuntu2.3_arm64.deb ...
Unpacking libpam-modules:arm64 (1.1.8-3.2ubuntu2.3) over (1.1.8-3.2ubuntu2.1) ...
Setting up libpam-modules:arm64 (1.1.8-3.2ubuntu2.3) ...
sed: cannot rename /etc/sedlVbCpt: Device or resource busy
dpkg: error processing package libpam-modules:arm64 (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 libpam-modules:arm64
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/LEFT]


---

