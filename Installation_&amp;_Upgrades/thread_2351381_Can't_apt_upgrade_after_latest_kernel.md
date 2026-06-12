---
title: "Can't apt upgrade after latest kernel"
date: 2017-02-02
forum: Installation &amp; Upgrades
---

### Post by ameenshake on 2017-02-02
Hi All,

I am running Ubuntu 16.10. I upgrade to the latest kernel but some then this happened. Whenever I run apt autoremove or apt install, im met with a plethora of error messages;

```
$sudo apt autoremove

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-59-generic linux-image-extra-4.4.0-59-generic
0 upgraded, 0 newly installed, 2 to remove and 4 not upgraded.
9 not fully installed or removed.
After this operation, 219 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 522644 files and directories currently installed.)
Removing linux-image-extra-4.4.0-59-generic (4.4.0-59.80) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-59-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
Error! Your kernel headers for kernel 4.4.0-59-generic cannot be found.
Please install the linux-headers-4.4.0-59-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-59-generic cannot be found.
Please install the linux-headers-4.4.0-59-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
WARNING: missing /lib/modules/4.4.0-59-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-59-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_OSE5Px/lib/modules/4.4.0-59-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_OSE5Px/lib/modules/4.4.0-59-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: 2009: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-59-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-59-generic (4.4.0-59.80) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-59-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: 2009: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-59-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-59-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.4.0-59-generic
 linux-image-4.4.0-59-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

```
$sudo dpkg -C

The following packages have been unpacked but not yet configured.They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-generic        Complete Generic Linux kernel and headers
 linux-image-extra-4.8.0-37-generic Linux kernel extra modules for version 4.8.
 linux-image-generic  Generic Linux kernel image
 linux-signed-generic Complete Signed Generic Linux kernel and headers
 linux-signed-image-4.8.0-37-generic Signed kernel image generic
 linux-signed-image-generic Signed Generic Linux kernel image


The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 linux-image-4.8.0-37-generic Linux kernel image for version 4.8.0 on 64 bit x8


The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-image-4.4.0-59-generic Linux kernel image for version 4.4.0 on 64 bit x8
 linux-image-extra-4.4.0-59-generic Linux kernel extra modules for version 4.4.


 
```
```
$uname -a

Linux 4.8.0-34-generic #36-Ubuntu SMP Wed Dec 21 17:24:18 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

Please let me know if you need other information. 

Thank you so much for your help guys!

---

