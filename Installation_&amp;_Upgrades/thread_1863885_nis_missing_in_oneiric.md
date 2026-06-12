---
title: "nis missing in oneiric?"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by cspence on 2011-10-18
Hi, I recently upgraded to from 11.04 to 11.10, on a 64-bit machine. The machine is connected to a network that uses NIS for the usual things, passwords, nfs mounts, etc. NIS seems to be gone in the upgrade, and the package manager can't seem to find it. For example:

> clay@cholla:~$ uname -a
Linux cholla 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
clay@cholla:~$ ypwhich
The program 'ypwhich' is currently not installed.  You can install it by typing:
sudo apt-get install nis
clay@cholla:~$ sudo apt-get install nis
[sudo] password for clay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nis is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  hostname:i386 hostname

E: Package 'nis' has no installation candidate

The Ubuntu Software Center doesn't seem to know about a package containing NIS, either. My home directory is set up to be autmounted, which isn't working I assume because of the lack of NIS.

---

### Post by cspence on 2011-10-25
This appears to have been a problem with the package management system or the new (?) update manager.

From a suggestion on a different thread (which I now can't find; sorry) I started the update manager, clicked the Settings button, selected the "Ubuntu Software" tab, selected "Download from ...", "Other ...", and then "Select best server". When this was done, I could install synaptic with the Ubuntu software center. I think the software center still could not find nis, but I'm not certain that I remember this correctly. Synaptic found nis, and I installed it.

---

