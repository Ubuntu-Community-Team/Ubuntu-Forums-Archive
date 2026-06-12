---
title: "can no longer run Update Manager successfully"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by billo38 on 2008-03-27
I have tried to run the update manager and I get the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 

So I run the "dpkg" command and get the following:

:~# dpkg --configure -a 
"Setting up initramfs-tools (0.85eubuntu20) ... 
update-initramfs: deferring update (trigger activated) 

Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic 
Cannot find /lib/modules/2.6.20-15-generic 
update-initramfs: failed for /boot/initrd.img-2.6.20-15-generic 
dpkg: subprocess post-installation script returned error exit status 1" 

The generic that is currently running on my machine is initrd.img-2-6-22-14-generic

There is no file on the system containing the phrase "2.6.20-15-generic"

How can I get past this problem?

billo38

---

### Post by wolfen69 on 2008-03-27
go to software sources and enable cd rom. just insert ubuntu cd and run sudo dpkg --configure -a  again.

---

### Post by billo38 on 2008-04-03
I have followed instructions, "go to software sources and enable cd rom. just insert ubuntu cd and run sudo dpkg --configure -a again."  I still get the error message - " Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
Cannot find /lib/modules/2.6.20-15-generic
update-initramfs: failed for /boot/initrd.img-2.6.20-15-generic
dpkg: subprocess post-installation script returned error exit status 1"

As far as I know inittrd.img-2.6.20-15-generic was never installed in this machine.  The only kernels that are currently loaded are 2.6.20-16-generic and 2.6.22-14-generic.
billo38

---

