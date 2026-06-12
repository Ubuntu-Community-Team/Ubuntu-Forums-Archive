---
title: "Error on uninstall of virtualbox,"
date: 2015-12-25
forum: Installation &amp; Upgrades
---

### Post by Johnny_P on 2015-12-25
Good afternoon,

I have installed on my laptop VirtualBox. After I upgrade/update new version, the virtual machine crash. The system use is represent by latest version of Ubuntu 64bit.

Everytime I try to update some software allready installed or to upgrade, the I receive the next error:

mefea@CAELinux:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following package was automatically installed and is no longer required:
  nvidia-opencl-icd-346-updates
Use 'apt-get autoremove' to remove it.
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**2 not fully installed or removed.**
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up virtualbox (4.3.34-dfsg-1+deb8u1ubuntu1.15.04.1) ...
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.3.34-dfsg-1+deb8u1ubuntu1.15.04.1); however:
  Package virtualbox is not configured yet.
  Package virtualbox-4.3 which provides virtualbox is not installed.


dpkg: error processing package virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
** virtualbox**
** virtualbox-qt**
E: Sub-process /usr/bin/dpkg returned an error code (1)
-------------------------------------------------------------------------------------------------

What I want to do, is to uninstall/remove the virtual machine. 
What is the command line from terminal which can offer me the possibility to uninstall/remove this 2 error?

I waiting with higher interest yours answers.
Best regards.

---

