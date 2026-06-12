---
title: "[SOLVED] Kernel cleanup"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by JustAnotherVagueAnon on 2008-10-14
My BOOT partition is 95% full so I think I must remove an older kernel to make room for the new one. I want to remove 2.6.24-18. Can I do this in Synaptic? If so, what do I search for and what all must I remove?

Here is a snippet from /boot/grub/menu.lst
```

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=a0369f42-e602-4e22-939f-85c97405ed65 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=a0369f42-e602-4e22-939f-85c97405ed65 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-18-generic root=UUID=a0369f42-e602-4e22-939f-85c97405ed65 ro quiet splash
initrd		/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.24-18-generic root=UUID=a0369f42-e602-4e22-939f-85c97405ed65 ro single
initrd		/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet

```

---

### Post by Partyboi2 on 2008-10-14
You can search for linux-image in synaptic and remove the kernels you know longer want. I would suggest keeping the one prior to the version you are currently using as well as the current one.

---

### Post by JustAnotherVagueAnon on 2008-10-14
When I tried to remove .18 I got this message:

E: linux-ubuntu-modules-2.6.24-18-generic: subprocess post-removal script returned error exit status 1

What can I do?

---

### Post by JustAnotherVagueAnon on 2008-10-14
I get this if I try autoremove now
```

bbraun@bbraun-desktop:~$ sudo apt-get autoremove
[sudo] password for bbraun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-18-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 17.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 166174 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-18-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-18-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by JustAnotherVagueAnon on 2008-10-14
And here is the output of dpkg --configure -a

```

bbraun@bbraun-desktop:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.24-21-generic (2.6.24-21.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-21-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.21.23); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-restricted-modules-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic

```

---

### Post by JustAnotherVagueAnon on 2008-10-14
Fixed. Synaptic and apt-get autoremove complained since the new kernel had been partially installed before it ran out of space (I'm guessing) so I apt-get remove'd the old kernel and then it would let me do the autoremove and reinstallation. Using 2.6.24-21 now ;)

---

