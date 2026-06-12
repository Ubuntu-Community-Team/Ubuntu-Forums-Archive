---
title: "Blank screen: 10.04, Dell T105(x86_64) and Nvidia 9400 GT"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by hsnewman on 2010-05-09
I installed 10.04 on my Dell T105, first via upgrade, then reinstalled.

I reinstalled because my Nvidia 9400 GT PCI goes blank on reboot.  

I've had to remove it to use the system, leaving me in 2d mode. 

I've tried the card with both VGA and DVI cables, without success.

I've edited the grub2 boot parms to not have "quiet splash", still without success.  I've also added "nomodeset", and several other parms such as "single", "nouveau.modeset=0/1", etc. 

NOTHING WORKS.  This card worked fine under all previous Ubuntu versions, as long as I had "quiet splash" removed.   

Ideas?

---

### Post by hsnewman on 2010-05-12
FYI this fixed it:

sudo gedit /etc/modprobe.d/blacklist.conf

At the end of this file, paste the following:
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

then uninstall all nvidia drivers

then reboot to command line

install NVIDIA-Linux-x86_64-195.36.24-pkg2.run

Now have 3d with compiz etc.

---

### Post by Catharsis on 2010-05-12
Please mark this thread as solved through "Thread Tools" at the top.

---

