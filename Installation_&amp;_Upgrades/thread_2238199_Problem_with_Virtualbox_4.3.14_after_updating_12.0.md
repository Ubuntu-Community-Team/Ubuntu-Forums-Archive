---
title: "Problem with Virtualbox 4.3.14 after updating 12.04.4 to Trusty HWE"
date: 2014-08-06
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2014-08-06
I upgraded my 12.04.4 x64 HWE to Trusty, and my Virtualbox 4.1.12 no longer ran.  I removed the 4.1.12 Virtualbox and installed the latest from the Virtualbox site, 4.3.14.  Now my XP VM runs, but the desktop opens with only a part of it showing.  The task bar at the bottom shows no prompts when I move the cursor over them.  If I go to the Start icon, the pop-up menu only partial appears.  When I move the cursor over the menu, some of the items previously not displayed become visable.  If I open an application, only part of the window will show.  If I attempt to move the window on the desktop, I get a trail of portions of the window.

Here is my vbox-install-log```
Uninstalling modules from DKMS
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.3.14/source ->
                 /usr/src/vboxhost-4.3.14

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.13.0-32-generic -C /lib/modules/3.13.0-32-generic/build M=/var/lib/dkms/vboxhost/4.3.14/build..........
cleaning build area....

DKMS: build completed.

vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-32-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-32-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-32-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-32-generic/updates/dkms/

depmod....

DKMS: install completed.
```My dkms version is 2.2.0.3-1ubuntu3.2.  I do not have a virtualbox-dkms for this version of Virtualbox.  It seems that either the dkms version is a mismatch for this kernel or there should be a virtualbox-dkms.  Any idess?

---

### Post by cscj01 on 2014-08-08
I just checked and found out that the Nouveau driver and associated files were installed.  However, I also have the latest Nvidia driver (334.21) installed manually.  I had to install the Nvidia driver because I have an EVA Geforce GTX 750 TI card, and the Nouveau driver would not support that card when I first installed it while on 12.04.4.  I also had to purge all my nouveau* files as well as xserver-xorg-video-nouveau.  I also added the following to my /etc/modeprobe.d/blacklist.conf file:> blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv It seems that when I upgraded my HWE, the Nouveau driver and files were installed.  Now I am wondering if this is my problem with my VM.  Any thoughts anyone?  Thanks for any help.

BTW, I also see this> Graphics   Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)when I view Applications>System Tools>System Settings>Details

---

### Post by cscj01 on 2014-08-09
I solved this by removing all PPA's with purge-ppa.  I'm not sure which one did it, but things work now.

---

