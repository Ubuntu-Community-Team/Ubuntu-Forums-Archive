---
title: "Video Display Flipping during install"
date: 2005-08-13
forum: Installation &amp; Upgrades
---

### Post by eleland on 2005-08-13
Hi,

New to ubuntu, and linux installs generally.  Apologies if this question has been answered.

I tried to run the ubuntu 5.04 install on a Dell Latitute CP PIII machine using all default settings, new partitions (not a dual boot, only ubuntu). It got through to the reboot, then after about 15 minutes of the second stage install the screen began to flip.   I restarted the machine and the install and the same occured.  Any thoughts on how to troubleshoot?  Thanks!

- Eric

---

### Post by PeP on 2005-08-13
try to reinstall

if you really want ubuntu, and the reinstallation did not solve your problem, boot from the live cd, 
mount your root hard drive,
open a terminal
chroot to the mount point (chroot /mnt/hda1)
get lilo and install it instead of grub.

an easier solution, try an other distribution (?debian?), you can even switch once it 's installed.

---

