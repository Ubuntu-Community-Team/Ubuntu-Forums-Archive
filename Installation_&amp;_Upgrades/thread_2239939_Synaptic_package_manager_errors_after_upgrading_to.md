---
title: "Synaptic package manager errors after upgrading to 14.04, BrokenCount&gt;0"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by bobmounger on 2014-08-16
Greetings, 

This is a gateway laptop dual booting windows 8 There is a red circle with a white minus sign next to the wifi icon in the title bar. I am running the Gnome desktop.

It told me to run the package manager & it failed with these details.

Thanks for any suggestion





(synaptic:16895): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
dpkg: warning: files list file for package 'mbrola' missing; assuming package has no files currently installed
(Reading database ... 1200848 files and directories currently installed.)
Removing linux-image-extra-3.13.0-33-generic (3.13.0-33.58) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-33-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-33-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-33-generic (3.13.0-33.58) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-33-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-33-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.2.0-30-generic (3.2.0-30.48) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.2.0-31-generic (3.2.0-31.50) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-31-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-31-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-32-generic (3.2.0-32.51) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-32-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-32-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-33-generic (3.2.0-33.52) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-33-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-33-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-34-generic (3.2.0-34.53) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-34-generic /boot/vmlinuz-3.2.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-34-generic /boot/vmlinuz-3.2.0-34-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-34-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-34-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-35-generic (3.2.0-35.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-36-generic (3.2.0-36.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-37-generic (3.2.0-37.58) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-37-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-37-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-38-generic (3.2.0-38.61) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-39-generic (3.2.0-39.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-39-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-39-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-39-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.13.0-33-generic
 linux-image-3.13.0-33-generic
 linux-image-3.2.0-30-generic
 linux-image-3.2.0-31-generic
 linux-image-3.2.0-32-generic
 linux-image-3.2.0-33-generic
 linux-image-3.2.0-34-generic
 linux-image-3.2.0-35-generic
 linux-image-3.2.0-36-generic
 linux-image-3.2.0-37-generic
 linux-image-3.2.0-38-generic
 linux-image-3.2.0-39-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up memtest86+ (4.20-1.1ubuntu8) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
dpkg: error processing package memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 64
Setting up grub-pc (2.02~beta2-9ubuntu1) ...
Installation finished. No error reported.

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 64
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on memtest86+; however:
  Package memtest86+ is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.13.0-34-generic (3.13.0-34.60) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.13.0-34-generic
) points to /boot/initrd.img-3.13.0-34-generic
 (/boot/initrd.img-3.13.0-34-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-34-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.13.0-34-generic
) points to /boot/vmlinuz-3.13.0-34-generic
 (/boot/vmlinuz-3.13.0-34-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-34-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
Warning: No support for locale: en_US.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-34-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-34-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-34-generic; however:
  Package linux-image-3.13.0-34-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-34-generic:
 linux-image-extra-3.13.0-34-generic depends on linux-image-3.13.0-34-generic; however:
  Package linux-image-3.13.0-34-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-34-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.34.40); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 memtest86+
 grub-pc
 ubuntu-desktop
 linux-image-3.13.0-34-generic
 linux-image-generic
 linux-image-extra-3.13.0-34-generic
 linux-generic

---

### Post by fantab on 2014-08-16
Please wrap the output of 'terminal' in ```
.

You seem to have several old kernels, which appear to have filled up the space.
Make space by removing old kernels...

Run:
[code]sudo update-grub
```
Note the latest Linux-Kernel.

Restart Ubuntu.

Run:
```
uname -r
```

It shows the kernel you have booted. Match the latest kernel and the output of uname-a.

Now to remove the older kernels:
```
sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

Reboot.

Run:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

If the output reports any errors post it here (in codes. See [here]("http://awesomescreenshot.com/0823bpnec1")).
If NOT then you are good.

---

### Post by bobmounger on 2014-08-17
sudo update-grub produces:

```
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.

```

uname -r produces:

```
3.2.0-57-generic
```

This is a long way from the most recent. 3.13.xxx

sudo dpkg... yields:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gcc-multilib : Depends: linux-libc-dev (>= 3.0.0-2) but it is not going to be installed
                PreDepends: linux-libc-dev (>= 2.6.38-8.42) but it is not going to be installed
 libc6-dev : Depends: linux-libc-dev but it is not going to be installed
 linux-headers-generic : Depends: linux-headers-3.13.0-34-generic but it is not going to be installed
 mbrola-en1 : Depends: mbrola
 mbrola-fr4 : Depends: mbrola
 mbrola-la1 : Depends: mbrola
 mbrola-us1 : Depends: mbrola
 mbrola-us2 : Depends: mbrola
 mbrola-us3 : Depends: mbrola
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

rebooted then the upgrade command
sudo apt-get update && sudo apt-get dist-upgrade

```

Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Ign http://archive.ubuntu.com trusty InRelease                                 
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Ign http://archive.ubuntu.com trusty-backports InRelease                       
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://deb.opera.com stable InRelease                                      
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.ubuntu.com trusty-proposed InRelease                        
Hit http://archive.ubuntu.com trusty Release.gpg                               
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Ign http://dl.google.com stable/main Translation-en_US                         
Get:1 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Hit http://deb.opera.com stable InRelease                                      
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.ubuntu.com trusty-backports Release.gpg                     
Hit http://security.ubuntu.com trusty-security Release                         
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Get:2 http://archive.ubuntu.com trusty-proposed Release.gpg [933 B]  
Hit http://ppa.launchpad.net trusty Release                          
Hit http://archive.ubuntu.com trusty Release                                   
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Get:3 http://archive.ubuntu.com trusty-updates Release [59.7 kB]               
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports Release                         
Get:4 http://archive.ubuntu.com trusty-proposed Release [110 kB]               
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://deb.opera.com stable/non-free i386 Packages                       
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages       
Hit http://security.ubuntu.com trusty-security/universe i386 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages       
Hit http://security.ubuntu.com trusty-security/main Translation-en            
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://archive.ubuntu.com trusty/main amd64 Packages                       
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US            
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages        
Hit http://archive.ubuntu.com trusty/universe amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Ign http://ppa.launchpad.net trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty/restricted i386 Packages
Hit http://archive.ubuntu.com trusty/universe i386 Packages
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/multiverse Translation-en
Ign http://deb.opera.com stable/non-free Translation-en_US
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-en
Ign http://deb.opera.com stable/non-free Translation-en
Get:5 http://archive.ubuntu.com trusty-updates/main amd64 Packages [293 kB]
Ign http://deb.opera.com stable/non-free Translation-en_US
Ign http://deb.opera.com stable/non-free Translation-en 
Get:6 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [5,820 B]
Get:7 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [181 kB]
Get:8 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [8,221 B]
Get:9 http://archive.ubuntu.com trusty-updates/main i386 Packages [289 kB]     
Get:10 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:11 http://archive.ubuntu.com trusty-updates/universe i386 Packages [182 kB]
Get:12 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [8,437 B]
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages             
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages         
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages              
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages          
Hit http://archive.ubuntu.com trusty-backports/main Translation-en             
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en       
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en         
Get:13 http://archive.ubuntu.com trusty-proposed/restricted amd64 Packages [14 B]
Get:14 http://archive.ubuntu.com trusty-proposed/main amd64 Packages [144 kB]  
Get:15 http://archive.ubuntu.com trusty-proposed/multiverse amd64 Packages [1,313 B]
Get:16 http://archive.ubuntu.com trusty-proposed/universe amd64 Packages [35.8 kB]
Get:17 http://archive.ubuntu.com trusty-proposed/restricted i386 Packages [14 B]
Get:18 http://archive.ubuntu.com trusty-proposed/main i386 Packages [139 kB]   
Get:19 http://archive.ubuntu.com trusty-proposed/multiverse i386 Packages [1,313 B]
Get:20 http://archive.ubuntu.com trusty-proposed/universe i386 Packages [35.9 kB]
Hit http://archive.ubuntu.com trusty-proposed/main Translation-en              
Hit http://archive.ubuntu.com trusty-proposed/multiverse Translation-en        
Hit http://archive.ubuntu.com trusty-proposed/restricted Translation-en        
Hit http://archive.ubuntu.com trusty-proposed/universe Translation-en          
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 1,502 kB in 17s (86.2 kB/s)                                            
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mbrola-en1 : Depends: mbrola
 mbrola-fr4 : Depends: mbrola
 mbrola-la1 : Depends: mbrola
 mbrola-us1 : Depends: mbrola
 mbrola-us2 : Depends: mbrola
 mbrola-us3 : Depends: mbrola
E: Unmet dependencies. Try using -f.

```

then per computer suggestion sudo apt-get -f install 
```

Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-32-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-32-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-33-generic (3.2.0-33.52) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-33-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-33-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-34-generic (3.2.0-34.53) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-34-generic /boot/vmlinuz-3.2.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-34-generic /boot/vmlinuz-3.2.0-34-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-34-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-34-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-35-generic (3.2.0-35.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-36-generic (3.2.0-36.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-37-generic (3.2.0-37.58) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-37-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-37-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-38-generic (3.2.0-38.61) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-38-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.2.0-39-generic (3.2.0-39.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-39-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
cat: /video.lst: No such file or directory
/usr/sbin/grub-probe: error: failed to get canonical path of `'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-39-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-39-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.13.0-33-generic
 linux-image-3.13.0-33-generic
 linux-image-3.2.0-30-generic
 linux-image-3.2.0-31-generic
 linux-image-3.2.0-32-generic
 linux-image-3.2.0-33-generic
 linux-image-3.2.0-34-generic
 linux-image-3.2.0-35-generic
 linux-image-3.2.0-36-generic
 linux-image-3.2.0-37-generic
 linux-image-3.2.0-38-generic
 linux-image-3.2.0-39-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It overflowed my terminal window, is this enough or should I pipe it to a file & paste that?

Thanks for your help.

---

### Post by fantab on 2014-08-18
What I can't understand is why you have 3.2Kernels when you should have 3.13 kernel.

By the way the latest kernel you have is 3.13.0-34 but you are booting 3.2.0-57.

If you want to keep things simple, I'd suggest have good backups of your DATA and you re-install Ubuntu.

---

