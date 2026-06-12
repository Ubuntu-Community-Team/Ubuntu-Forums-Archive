---
title: "Problem with update"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by toyonut on 2008-03-16
I tried to compile the latest kernel (2.6.24.2) a while ago and due to it failing, I removed it, but just about 5 mins ago, I tried to update software through synaptic and got a message telling me to manually run "dpkj --configure -a". I did that and it turns up this in the console
"paul@paul-laptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24.2
Cannot find /lib/modules/2.6.24.2
update-initramfs: failed for /boot/initrd.img-2.6.24.2
dpkg: subprocess post-installation script returned error exit status 1"

Synaptic is now down for the count, and I dont know how to remove anymore links to the now removed kernel.

I am running Mint 4.0 (gutsy with a facelift) and kernel 2.6.22.14. 

Thanks
Paul

---

