---
title: "Problems with package manager and upgrading"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by markusg on 2006-12-05
Hi,

Im new to Linux and a fresh Ubuntu user. Im using
the Breezy version with fluxbox on my laptop.
Suddently i have encoutered strange problems with the
package-system. Im not able to install anything, neither
to do an upgrade. 
When im typing the command for uprading:
"sudo apt-get upgrade"
I get this:

Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-restricted-modules-386 update-manager
The following packages will be upgraded:
  tar
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/520kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
(Reading database ... 83221 files and directories currently installed.)
Preparing to replace tar 1.15.1-2ubuntu0.1 (using .../tar_1.15.1-2ubuntu0.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/tar_1.15.1-2ubuntu0.2_i386.deb (--unpack):
 dpkg: warning - old pre-removal script killed by signal (Segmentation fault)

dpkg: error while cleaning up:
 subprocess post-installation script killed by signal (Segmentation fault)
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.15.1-2ubuntu0.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I can see theres some problem with the tar package, but havent succeeded
upgrading/removing/installing it with apt-get, aptitude, synaptics nor update-manager. 

Have anobody some hints on how too solve this issue?

---

### Post by markusg on 2006-12-09
Please, does anybody have som advice for me?

---

### Post by jcrnan on 2006-12-11
I think I might have a similar problem: [http://ubuntuforums.org/showthread.php?t=316949](http://ubuntuforums.org/showthread.php?t=316949)

---

### Post by Cal1066 on 2006-12-21
Same problem here...tar cannot be upgraded for the security release, which is tar_1.15.91-2ubuntu0.3_i386.deb.  Error says subprocess new pre-removal script returned error exit status 2, but the detail indicates it is trying to get the old process to do something and when that does not work the new process cannot be installed...something about being "...unable to execute old pre-removal script"  Can create error on my machine (6.10 just installed as a new install) by trying to install apt-doc.  But all 60 of the updates to this new installation fail due to this error!

---

