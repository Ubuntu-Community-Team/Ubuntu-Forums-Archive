---
title: "Installation or Removal of a Software Package Failed"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by gr34t3st on 2011-01-29
Hey, I'm having some issues with general installation and removal of apps. I'm not sure what changes I made to cause this because I'm not entirely sure when it started happening. Whenever I try to install or remove a package, I get this error.

```
installArchives() failed: Selecting previously deselected package airstrike-common.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 224643 files and directories currently installed.)
Unpacking airstrike-common (from .../airstrike-common_0.99+1.0pre6a-4_all.deb) ...
Selecting previously deselected package airstrike.
Unpacking airstrike (from .../airstrike_0.99+1.0pre6a-4_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for python-support ...
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
 * dkms: running auto installation service for kernel 2.6.35-24-generic

 *       nvidia-current (270.18)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-24-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic

 *       nvidia-current (270.18)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up airstrike-common (0.99+1.0pre6a-4) ...
Setting up airstrike (0.99+1.0pre6a-4) ...
Errors were encountered while processing:
 linux-image-2.6.35-24-generic
 linux-image-2.6.35-25-generic
 linux-image-generic
 linux-generic
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
 * dkms: running auto installation service for kernel 2.6.35-24-generic

 *       nvidia-current (270.18)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-24-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic

 *       nvidia-current (270.18)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured

```

I get this error every time I run Update Manager. Despite this error, the installations always seem to work properly. The only exception I have is when I tried installing DKMS for Virtualbox. When I received the error in that install, Virtualbox still gave me a DKMS error. Thanks in advance for the help...

---

### Post by jetcoasterlove on 2011-07-12
> **gr34t3st said:**
> Hey, I'm having some issues with general installation and removal of apps. I'm not sure what changes I made to cause this because I'm not entirely sure when it started happening. Whenever I try to install or remove a package, I get this error.

```
installArchives() failed: Selecting previously deselected package airstrike-common.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 224643 files and directories currently installed.)
Unpacking airstrike-common (from .../airstrike-common_0.99+1.0pre6a-4_all.deb) ...
Selecting previously deselected package airstrike.
Unpacking airstrike (from .../airstrike_0.99+1.0pre6a-4_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for python-support ...
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
 * dkms: running auto installation service for kernel 2.6.35-24-generic

 *       nvidia-current (270.18)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-24-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic

 *       nvidia-current (270.18)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up airstrike-common (0.99+1.0pre6a-4) ...
Setting up airstrike (0.99+1.0pre6a-4) ...
Errors were encountered while processing:
 linux-image-2.6.35-24-generic
 linux-image-2.6.35-25-generic
 linux-image-generic
 linux-generic
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
 * dkms: running auto installation service for kernel 2.6.35-24-generic

 *       nvidia-current (270.18)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-24-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic

 *       nvidia-current (270.18)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured

```I get this error every time I run Update Manager. Despite this error, the installations always seem to work properly. The only exception I have is when I tried installing DKMS for Virtualbox. When I received the error in that install, Virtualbox still gave me a DKMS error. Thanks in advance for the help...

I'm actually going through the same issue here, it would be great if someone would help us get through this. I can't even make updates correctly now because of that error 

:confused:

---

