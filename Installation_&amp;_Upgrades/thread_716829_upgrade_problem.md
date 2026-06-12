---
title: "upgrade problem"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by billo38 on 2008-03-06
When I try to install updates I receive the following error message:
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
When I run the "dpkg" command I receive the following error message:
"Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
Cannot find /lib/modules/2.6.20-15-generic
update-initramfs: failed for /boot/initrd.img-2.6.20-15-generic
dpkg: subprocess post-installation script returned error exit status 1"

I have searched for the "2.6.20-15-generic" file using the "find" command but the file cannot be located.  How do I get a copy of the file?
Thanks,  Bill

---

### Post by mikewhatever on 2008-03-07
Try here [http://packages.ubuntu.com/feisty/linux-image-2.6.20-15-generic](http://packages.ubuntu.com/feisty/linux-image-2.6.20-15-generic)

Here is a direct link to x32 version [http://packages.ubuntu.com/feisty/i386/linux-image-2.6.20-15-generic/download](http://packages.ubuntu.com/feisty/i386/linux-image-2.6.20-15-generic/download)

PS: > upgrade problem
When I try to install updates I receive the following error message:

Are you updating or upgrading?

---

### Post by billo38 on 2008-03-17
I am currently running on 2.6.22-14-generic.
prior to that I was running 2.6.20-16-generic.  Why is the system calling for 2.6.20-15?
Bill

---

