---
title: "strange and deep probleme with kernel"
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by papilonaa on 2015-01-09
there are a lot of errors with keys and when i try to update and upgrade after installing a few programs
But then i update the kernel via synaptic and since then...it does want to install anythings..and tell me to delete..the 3.13.0-40  kernel...i am i am on trusty and running on 3.13.0-39 kernel right now....i did install the -40 and -43 stupidly and  i  cannot get reed of it..
.thanks a lot for help..
please

[HTML][sudo] password for dom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-panel is already the newest version.
gnome-panel set to manually installed.
The following packages will be REMOVED:
  linux-image-3.13.0-40-generic linux-image-3.13.0-40-lowlatency
  linux-image-extra-3.13.0-40-generic
0 upgraded, 0 newly installed, 3 to remove and 29 not upgraded.
11 not fully installed or removed.
After this operation, 387 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 361530 files and directories currently installed.)
Removing linux-image-extra-3.13.0-40-generic (3.13.0-40.69) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-40-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
Error! Your kernel headers for kernel 3.13.0-40-generic cannot be found.
Please install the linux-headers-3.13.0-40-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-40-generic cannot be found.
Please install the linux-headers-3.13.0-40-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-40-generic
grep: /boot/config-3.13.0-40-generic: No such file or directory
WARNING: missing /lib/modules/3.13.0-40-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-40-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_4akACS/lib/modules/3.13.0-40-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_4akACS/lib/modules/3.13.0-40-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-43-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-43-generic...
P: Writing config for /boot/vmlinuz-3.13.0-39-generic...
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_CMDLINE_LINUX_DEFAULT=drm.debug=0xe plymouth:debug'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.13.0-40-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-40-generic (3.13.0-40.69) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-43-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-43-generic...
P: Writing config for /boot/vmlinuz-3.13.0-39-generic...
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_CMDLINE_LINUX_DEFAULT=drm.debug=0xe plymouth:debug'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-40-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-40-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-40-lowlatency (3.13.0-40.69) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-40-lowlatency /boot/vmlinuz-3.13.0-40-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.13.0-40-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-40-lowlatency /boot/vmlinuz-3.13.0-40-lowlatency
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-43-lowlatency...
P: Writing config for /boot/vmlinuz-3.13.0-43-generic...
P: Writing config for /boot/vmlinuz-3.13.0-39-generic...
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-40-lowlatency /boot/vmlinuz-3.13.0-40-lowlatency
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_CMDLINE_LINUX_DEFAULT=drm.debug=0xe plymouth:debug'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-40-lowlatency.postrm line 328.
dpkg: error processing package linux-image-3.13.0-40-lowlatency (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-40-generic
 linux-image-3.13.0-40-generic
 linux-image-3.13.0-40-lowlatency
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML]

---

