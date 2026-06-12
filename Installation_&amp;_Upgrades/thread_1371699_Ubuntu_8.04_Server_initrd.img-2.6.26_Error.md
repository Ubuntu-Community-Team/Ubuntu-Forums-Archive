---
title: "Ubuntu 8.04 Server initrd.img-2.6.26 Error"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by haritsu on 2010-01-03
Hello Guys,

I have a server with Intel Core i7 processor. During the first update after installation, I encountered a problem.

This command and after;
```
root@node:~# aptitude install bind8
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```dpkg --configure -a run command and after;
```
root@node:~# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.26
Cannot find /lib/modules/2.6.26
update-initramfs: failed for /boot/initrd.img-2.6.26
dpkg: subprocess post-installation script returned error exit status 1
```How can I solve this problem?

uname -a output
```
root@node:~# uname -a
Linux node.halid.org 2.6.28.7 #1 SMP Fri Mar 20 09:23:58 EDT 2009 i686 GNU/Linux
```Thank you for your answers...

---

### Post by zvacet on 2010-01-04
```
sudo dpkg --configure -a
```

---

