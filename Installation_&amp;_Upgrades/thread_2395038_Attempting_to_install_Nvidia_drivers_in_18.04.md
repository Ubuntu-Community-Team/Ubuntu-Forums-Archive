---
title: "Attempting to install Nvidia drivers in 18.04"
date: 2018-06-25
forum: Installation &amp; Upgrades
---

### Post by TigrisAltaica on 2018-06-25
Hello! I'm trying to install Ubuntu 18.04 on a new HP Pavilion laptop. After a few failed attempts I found out about using nomodeset and managed to get the installation up and running. The stuff I found mentioned that I should go ahead and install the Nvidia driviers manually to fix the problem for good. I'm trying to but the installation keeps running into the same problem:
> 
Processing triggers for initramfs-tools (0.130ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-23-generic
Setting up nvidia-dkms-390 (390.48-0ubuntu3) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG : Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG : Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG : Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Removing old nvidia-390.48 DKMS files...

-------- Uninstall Beginning --------
Module:  nvidia
Version: 390.48
Kernel:  4.15.0-23-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 390.48
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-390.48 DKMS files...
Building for 4.15.0-23-generic
Building for architecture x86_64
Building initial module for 4.15.0-23-generic


It just stays there. I've tried closing the terminal but then I can't use apt-get as it tells me to :

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


And then the whole thing repeats. Thank you in advance for your help.

---

### Post by ubfan1 on 2018-06-25
How long did you wait?  It might take a few minutes to build the module.

---

### Post by TigrisAltaica on 2018-06-25
Maybe 40 minutes?

---

