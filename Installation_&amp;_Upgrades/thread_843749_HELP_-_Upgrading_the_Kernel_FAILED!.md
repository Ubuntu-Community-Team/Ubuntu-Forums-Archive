---
title: "HELP - Upgrading the Kernel FAILED!"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Maverick88 on 2008-06-28
I have been running Hardy Herom for awhile.  I just checked for updates and applied them using Synaptic Package Manager. But the update for the Kernel and Kernel Modules failed.  Synaptic gave me the following error message.

E: linux-image-2.6.24-19-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-19-generic: dependency problems - leaving unconfigured

I tried to reinstall these two packages.  No luck.  I get the same error message.

Any ideas on what I need to do to solve thie error?

---

### Post by Maverick88 on 2008-06-28
I found the problem.  After runnning "sudo apt-get upgrade" in the Terminal, I saw an error message stating that there was not enough space.  Sure enough my /boot partition was full.  

After deleting some old kernels and their related files from the /boot partition, I was able to successfully install the latest kernel and kernel modules by running "sudo apt-get upgrade" in the Terminal.

---

