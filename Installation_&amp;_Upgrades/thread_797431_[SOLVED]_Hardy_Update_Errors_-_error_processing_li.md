---
title: "[SOLVED] Hardy Update Errors - error processing linux-generic (--configure)"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by dickohead on 2008-05-17
I have had this issue for about a week now and have been unable to find a solution.

It appears that there is an error with /sbin/update-grub but I do not how to correct it.

My errors are:
```

Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-generic:
 linux-ubuntu-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-generic:
 linux-restricted-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-17-generic; however:
  Package linux-restricted-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.17.19); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-17-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-17-generic
 linux-restricted-modules-generic
 linux-generic

```

I have tried the following commands to try and correct it but to no avail:
```

sudo dpkg --configure -a

sudo aptitude autoclean

sudo apt-get install --reinstall linux-image-2.6.24-17-generic linux-ubuntu-modules-2.6.24-17-generic linux-image-generic linux-restricted-modules-2.6.24-17-generic linux-restricted-modules-generic linux-generic

sudo apt-get clean

```

This is a fairly fresh install, I've not even had a chance to add my own programs yet, everything installed has come from the repositories - official ones only (Australian mirrors though).

Now i think that this bit:
```

linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-17-generic; however:
  Package linux-restricted-modules-2.6.24-17-generic is not configured yet.

```
Might be of importance, but I've not been able to find any solutions nor figure out my own.

Is anyone able to help?

---

### Post by Cerin on 2008-05-30
I ran into this same error on the alternate install CD for 8.04. It completely kills the install.

---

### Post by Pumalite on 2008-05-30
Try sudo dpkg --configure linux-restricted-modules-2.6.24-17-generic
Or:
sudo dpkg --configure linux-image-2.6.24-17-generic

---

### Post by Cerin on 2008-05-30
> **Pumalite said:**
> Try sudo dpkg --configure linux-restricted-modules-2.6.24-17-generic
Or:
sudo dpkg --configure linux-image-2.6.24-17-generic

Thanks, I'll try that. However, why would this be occurring during install?

---

### Post by Cerin on 2008-05-30
Those don't work. The error occurs before dpkg is installed.

---

### Post by dickohead on 2008-05-31
I fixed mine by removing gfxboot and gfxboot-grub.

Apparently there is a problem with the grub-update file included with gfxboot!

All good now.

:D

---

### Post by Cerin on 2008-05-31
> **dickohead said:**
> I fixed mine by removing gfxboot and gfxboot-grub.

Apparently there is a problem with the grub-update file included with gfxboot!

All good now.

:D

I wouldn't begin to know how to do that during the install. The most frustrating part of this is that this bug was reported back in January, but it wasn't deemed worth fixing. I've giving up on Ubuntu until it's had a few more years to mature.

---

### Post by mario@chianti-doc.com on 2008-11-27
I can not upgrade the system anymore because i have dependency problems unable to configure:

root@AMD64:~# sudo dpkg --configure linux-image-2.6.27-10-generic
Setting up linux-image-2.6.27-10-generic (2.6.27-10.20) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.27-10-generic)
dpkg: error processing linux-image-2.6.27-10-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.27-10-generic
root@AMD64:~# sudo dpkg --configure linux-restricted-modules-2.6.27-10-generic
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-10-generic:
 linux-restricted-modules-2.6.27-10-generic depends on linux-image-2.6.27-10-generic; however:
  Package linux-image-2.6.27-10-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-10-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-2.6.27-10-generic


Any idea ?

thanks

---

### Post by Pumalite on 2008-11-27
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

