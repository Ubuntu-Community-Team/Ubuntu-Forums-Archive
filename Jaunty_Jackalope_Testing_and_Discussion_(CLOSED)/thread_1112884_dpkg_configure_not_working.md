---
title: "dpkg configure not working"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by amcvega on 2009-04-01
Hi,

I did my usual update this morning and the update manager said it completed and something failed.  When I tried installing something using aptitude I got this:

```

~ $ sudo aptitude install googlearth
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

When I tried running dpkg --configure -a I got this:

```

~ $ sudo dpkg --configure -a
[sudo] password for amcvega: 
Setting up initramfs-tools (0.92bubuntu26) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
cpio: ./lib/klibc-*.so: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: subprocess post-installation script returned error exit status 1

```

Has anyone run into a similar problem?

---

