---
title: "Crash when moving to anything newer than 4.4.0-21-generic"
date: 2018-01-11
forum: Installation &amp; Upgrades
---

### Post by Superdude_123 on 2018-01-11
I'm trying to figure out why when I run an apt-get disupgrade to upgrade my kernel to something newer than 4.4.0-21, my system will crash after some time of just being idle. My best guess is a kernel module not loading, however, is there a way to upgrade my kernel and have my modules/drivers load with the new kernel?

I tried running ```
sudo apt-get install linux-headers-4.4.0-109 linux-headers-4.4.0-109-generic linux-headers-generic linux-image-4.4.0-109-generic linux-image-extra-4.4.0-109-generic linux-image-generic linux-tools-4.4.0-109 linux-tools-4.4.0-109-generic linux-tools-generic 
``` to upgrade to the latest kernel, but by system still becomes unresponsive after sometime.

---

### Post by ubfan1 on 2018-01-11
Do you have any room left on root or boot for the new kernel?  Post the output of the df command to see.  Take a dir of /boot to see how many old kernels are there and need cleaning up.

---

### Post by thyrson on 2018-01-11
Hi,

Did you specifically want to upgrade the kernel? otherwise you can upgrade it with the version itself, at least I do it that way.

maybe it helps you even further, if you upgrade the system generally so far, that you have the latest kernel.
I selsbt also use 16.04.x and have so far carried out the upgrade to have the current module.

What might also be a clue for you, the updates for all new versions to record and then switch back to LTS.

I hope I could possibly help you further.

---

