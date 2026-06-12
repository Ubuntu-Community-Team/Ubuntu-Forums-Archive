---
title: "Upgrading to 9.10 - Can't remove headers"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by mgbaron on 2009-12-10
I just completed upgrading to 9.10 and the process hung at the very end removing some old Linux headers.  I had to kill the process, but now I can't get anymore updates because the headers were improperly cleaned up.  I tried removing them from the command line but it always hangs.  

How can I get rid of these headers once and for all?

Here is what I am doing:

matt@machine:~$ sudo dpkg --configure -a
matt@machine:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  g++-4.3 libmagickcore1 libmagickwand1 libstdc++6-4.3-dev
  linux-headers-2.6.28-15 nvidia-180-kernel-source nvidia-180-libvdpau
  qt4-qtconfig screen-profiles update-motd
0 upgraded, 0 newly installed, 10 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 93.5MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 181763 files and directories currently installed.)
Removing linux-headers-2.6.28-15 ...
^C^C^C^C^C^C^C^C^C^C^C^C^C^C^C^C^C^C^C^C^C^C^C^C^C^CE: Sub-process /usr/bin/dpkg exited unexpectedly
matt@machine:~$

---

