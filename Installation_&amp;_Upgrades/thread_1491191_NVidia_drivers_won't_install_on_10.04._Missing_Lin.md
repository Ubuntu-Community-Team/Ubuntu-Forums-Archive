---
title: "NVidia drivers won't install on 10.04. Missing Linux headers?"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by bartvh on 2010-05-23
I'm trying to install the current drivers (from the Hardware Drivers tool) but it fails, refering me to jockey.log, which contains this:

```
2010-05-23 16:19:46,978 DEBUG: nvidia_current is not the alternative in use
2010-05-23 16:19:47,106 DEBUG: nvidia_current is not the alternative in use
2010-05-23 16:20:02,225 DEBUG: Installing package: linux-headers-2.6.31-20-generic
2010-05-23 16:20:02,445 DEBUG: Package linux-headers-2.6.31-20-generic does not exist, aborting
2010-05-23 16:20:02,630 DEBUG: Installing package: nvidia-current
2010-05-23 16:20:03,120 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-05-23 16:20:03,368 DEBUG: install progress statusChange nvidia-current 0.000000
2010-05-23 16:20:03,470 DEBUG: install progress statusChange nvidia-current 10.000000
2010-05-23 16:20:12,600 DEBUG: install progress statusChange nvidia-current 20.000000
2010-05-23 16:20:12,614 DEBUG: install progress statusChange nvidia-current 30.000000
2010-05-23 16:20:12,666 DEBUG: install progress statusChange nvidia-settings 30.000000
2010-05-23 16:20:12,758 DEBUG: install progress statusChange nvidia-settings 40.000000
2010-05-23 16:20:12,758 DEBUG: install progress statusChange nvidia-settings 50.000000
2010-05-23 16:20:12,760 DEBUG: install progress statusChange nvidia-settings 60.000000
2010-05-23 16:20:12,767 DEBUG: install progress statusChange man-db 60.000000
2010-05-23 16:20:13,889 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-05-23 16:20:14,014 DEBUG: install progress statusChange nvidia-current 60.000000
2010-05-23 16:20:14,038 DEBUG: install progress statusChange nvidia-current 70.000000
2010-05-23 16:20:48,366 DEBUG: install progress statusChange nvidia-current 80.000000
2010-05-23 16:20:48,387 DEBUG: install progress statusChange nvidia-settings 80.000000
2010-05-23 16:20:48,388 DEBUG: install progress statusChange nvidia-settings 90.000000
2010-05-23 16:20:48,389 DEBUG: install progress statusChange nvidia-settings 100.000000
2010-05-23 16:20:48,391 DEBUG: install progress statusChange python-gmenu 100.000000
2010-05-23 16:20:48,523 DEBUG: install progress statusChange initramfs-tools 100.000000
2010-05-23 16:20:54,275 DEBUG: install progress statusChange python-support 100.000000
2010-05-23 16:20:55,881 DEBUG: Selecting previously deselected package nvidia-current.
(Reading database ... 174092 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_195.36.15-0ubuntu3_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (195.36.15-0ubuntu3) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Loading new nvidia-current-195.36.15 DKMS files...
Building for 2.6.31-20-generic and 2.6.32-22-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 2.6.32-22-generic
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-22-generic/updates/dkms/

depmod....

DKMS: install Completed.

Setting up nvidia-settings (195.36.08-0ubuntu2) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Processing triggers for python-support ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB


2010-05-23 16:20:56,100 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-23 16:20:56,101 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
```

What's happening? Is it because of "Package linux-headers-2.6.31-20-generic does not exist, aborting"?

---

### Post by bartvh on 2010-05-23
Solved. Apparently I was running on an old kernel due to a not updated menu.lst.

---

### Post by dino99 on 2010-05-23
> **bartvh said:**
> Solved. Apparently I was running on an old kernel due to a not updated menu.lst.

menu.lst need to be removed due to grub2 issues, then 

sudo update-grub
sudo update-initramfs -u

---

