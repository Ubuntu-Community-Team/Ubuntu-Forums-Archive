---
title: "errors after udating ubuntu studio"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by betrion on 2008-02-18
i cleanly installed ubuntu studio x64 and started update manager, and after updating i cant enter synaptic manager it says to sudo dpkg --configure -a, but after i do that..this is what i get:
```
dean@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for dean:
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

dpkg: dependency problems prevent configuration of linux-image-rt:
 linux-image-rt depends on linux-ubuntu-modules-2.6.22-14-rt; however:
  Package linux-ubuntu-modules-2.6.22-14-rt is not installed.
dpkg: error processing linux-image-rt (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-base-bin (2007-12ubuntu3.1) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-base-bin (--configure):
 subprocess post-installation script returned error exit status 127
Setting up linux-image-2.6.22-14-rt (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-rt (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-rt:
 linux-restricted-modules-2.6.22-14-rt depends on linux-image-2.6.22-14-rt; however:
  Package linux-image-2.6.22-14-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-14-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-rt:
 linux-restricted-modules-rt depends on linux-restricted-modules-2.6.22-14-rt; however:
  Package linux-restricted-modules-2.6.22-14-rt is not configured yet.
dpkg: error processing linux-restricted-modules-rt (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
dpkg: subprocess post-installation script returned error exit status 1
```

---

### Post by betrion on 2008-02-18
i restarted the computer and now i even lost sound.

---

