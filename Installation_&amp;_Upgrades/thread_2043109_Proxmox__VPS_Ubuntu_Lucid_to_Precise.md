---
title: "Proxmox  VPS: Ubuntu Lucid to Precise"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by dereks on 2012-08-15
Posting an issue and solution for the next victim.

As a Proxmox user, I run quite a few Ubuntu VPS's on a low end a cute little headless HP N36L beefed up to 4GB and 4 x 500GB disks - extremely cost efficient and space saving. My Ubuntu environments range from mail to forum and  bespoke applications. All my VPS's were Lucid.

Recently I had a requirement a 12.04 (Precise)  environment to emulate one of my production environments. With there not being a Proxmox 12.04 template, I tried creating my own own by starting off with 10.04 and upgrading.

For the bulk, this worked fine and I ended up with a workable VPS, except something was amiss, as can be seen when trying to add a package:

> # apt-get install ghostscript
Reading package lists... Done
Building dependency tree
Reading state information... Done
ghostscript is already the newest version.
ghostscript set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.2.0-24-generic (3.2.0-24.39) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled
(3.2.0-24.37 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(3.2.0-24.37 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic /bo                                                                                       ot/vmlinuz-3.2.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic /boo                                                                                       t/vmlinuz-3.2.0-24-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0                                                                                       -24-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-27-generic (3.2.0-27.43) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-27-generic /bo                                                                                       ot/vmlinuz-3.2.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-27-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-27-generic; however:
  Package linux-image-3.2.0-27-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.27.29); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
 Errors were encountered while processing:
 linux-image-3.2.0-24-generic
 linux-image-3.2.0-27-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


After digging into the issue, we do not need: grub2-common grub-pc grub-gfxpayload-lists
> dpkg -P  grub2-common grub-pc grub-gfxpayload-lists

Any package mangement worked as advertised after this, except for:
> The following packages were automatically installed and are no longer required:
  libfuse2 grub-pc-bin grub-common
Use 'apt-get autoremove' to remove them.


Which is exactly what I did and I'm happily running 12.04 now, no issues.

---

