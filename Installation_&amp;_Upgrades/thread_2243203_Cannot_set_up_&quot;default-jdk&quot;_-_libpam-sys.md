---
title: "Cannot set up &quot;default-jdk&quot; - libpam-systemd:armhf is not configured yet..."
date: 2014-09-07
forum: Installation &amp; Upgrades
---

### Post by Varga_Edmond on 2014-09-07
Hi,

I would like to install Tomcat7 on my sistem (Ubuntu 14.04 LTS), which I already did, but as I try to install "default-jdk" the process stops and I get the following message:

```
root@localhost:~# apt-get install default-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  default-jdk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/934 B of archives.
After this operation, 21.5 kB of additional disk space will be used.
Selecting previously unselected package default-jdk.
(Reading database ... 29887 files and directories currently installed.)
Preparing to unpack .../default-jdk_2%3a1.7-51_armhf.deb ...
Unpacking default-jdk (2:1.7-51) ...
Setting up libpam-systemd:armhf (204-5ubuntu20) ...
invoke-rc.d: unknown initscript, /etc/init.d/systemd-logind not found.
dpkg: error processing package libpam-systemd:armhf (--configure):
 subprocess installed post-installation script returned error exit status 100
dpkg: dependency problems prevent configuration of policykit-1:
 policykit-1 depends on libpam-systemd; however:
  Package libpam-systemd:armhf is not configured yet.


dpkg: error processing package policykit-1 (--configure):
 dependency problems - leaving unconfigured
Setting up default-jdk (2:1.7-51) ...
Errors were encountered while processing:
 libpam-systemd:armhf
 policykit-1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am quite new to ubuntu, but I would really like to learn more about it. Please help me out.
Thanks!

---

