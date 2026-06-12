---
title: "Samba installation fails"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by impartit on 2012-01-16
I get "Package Operation Failed" when attempting to install Samba within Ubuntu 11.10 running  on my dual boot Sony PCG 21313M notebook with Windows 7 Starter. The  problem persists even after running "sudo apt-get autoremove samba"  (twice). Am I just asking too much of the Atom N450 processor.

Details is:
Errors were encountered processing:
samba
system-config
Error in function
System Error E: Sub-process /usr/bin/dpkg returned and error code (1)
Setting up samba (2:3.5.11~dfsg-1ubuntu2.1
start Unknown job.smbd
invoke-rc.d initscript smbd, action start failed
dpkg: error processing samba (-configure):
subprocess installed post installation script returned error status exit status 1
dpkg: dependency problems prevent configuration of system-config-samba
system-config-samba depends on samba; however:
Package samba is not configured yet.
dpkg: error processing system-cinfig-samba (-configure):
dependency problems - leaving unconfigured.

Am I looking for a missing file "smbd" somewhere in the file system?



** **

---

