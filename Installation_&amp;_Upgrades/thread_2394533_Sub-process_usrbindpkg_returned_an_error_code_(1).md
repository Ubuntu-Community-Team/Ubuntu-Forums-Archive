---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2018-06-18
forum: Installation &amp; Upgrades
---

### Post by caplock on 2018-06-18
[SIZE=4]**I always got this when make updating at terminal. Kindly advise.**[/SIZE]


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-121-generic linux-image-4.4.0-124-generic linux-image-4.4.0-62-generic
  linux-image-4.4.0-93-generic linux-image-extra-4.4.0-121-generic linux-image-extra-4.4.0-124-generic
  linux-image-extra-4.4.0-93-generic
0 upgraded, 0 newly installed, 7 to remove and 3 not upgraded.
9 not fully installed or removed.
After this operation, 731 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 417837 files and directories currently installed.)
Removing linux-image-extra-4.4.0-121-generic (4.4.0-121.145) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-121-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-121-generic /boot/vmlinuz-4.4.0-121-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-121-generic /boot/vmlinuz-4.4.0-121-generic
Error! Your kernel headers for kernel 4.4.0-121-generic cannot be found.
Please install the linux-headers-4.4.0-121-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-121-generic cannot be found.
Please install the linux-headers-4.4.0-121-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-121-generic /boot/vmlinuz-4.4.0-121-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-121-generic
WARNING: missing /lib/modules/4.4.0-121-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-121-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
depmod: WARNING: could not open /var/tmp/mkinitramfs_bZsqZ1/lib/modules/4.4.0-121-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_bZsqZ1/lib/modules/4.4.0-121-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-121-generic /boot/vmlinuz-4.4.0-121-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-121-generic /boot/vmlinuz-4.4.0-121-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-121-generic /boot/vmlinuz-4.4.0-121-generic
run-parts: executing /etc/kernel/postinst.d/x-grub-legacy-ec2 4.4.0-121-generic /boot/vmlinuz-4.4.0-121-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
uuid not supported. update 'groot' in /boot/grub/menu.lst


groot must be grub root device (ie '(hd0)'). not 'a9a2880d-8432-4dec-a97e-a7de1c570ef3'


run-parts: /etc/kernel/postinst.d/x-grub-legacy-ec2 exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-121-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-121-generic (4.4.0-121.145) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-121-generic /boot/vmlinuz-4.4.0-121-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-121-generic
run-parts: executing /etc/kernel/postrm.d/x-grub-legacy-ec2 4.4.0-121-generic /boot/vmlinuz-4.4.0-121-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
uuid not supported. update 'groot' in /boot/grub/menu.lst


groot must be grub root device (ie '(hd0)'). not 'a9a2880d-8432-4dec-a97e-a7de1c570ef3'


run-parts: /etc/kernel/postrm.d/x-grub-legacy-ec2 exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-121-generic.postrm line 330.
dpkg: error processing package linux-image-4.4.0-121-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-124-generic (4.4.0-124.148) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-124-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-124-generic /boot/vmlinuz-4.4.0-124-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-124-generic /boot/vmlinuz-4.4.0-124-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-124-generic /boot/vmlinuz-4.4.0-124-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-124-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
depmod: WARNING: could not open /var/tmp/mkinitramfs_5NJ2MO/lib/modules/4.4.0-124-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_5NJ2MO/lib/modules/4.4.0-124-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-124-generic /boot/vmlinuz-4.4.0-124-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-124-generic /boot/vmlinuz-4.4.0-124-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-124-generic /boot/vmlinuz-4.4.0-124-generic
run-parts: executing /etc/kernel/postinst.d/x-grub-legacy-ec2 4.4.0-124-generic /boot/vmlinuz-4.4.0-124-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
uuid not supported. update 'groot' in /boot/grub/menu.lst


groot must be grub root device (ie '(hd0)'). not 'a9a2880d-8432-4dec-a97e-a7de1c570ef3'


run-parts: /etc/kernel/postinst.d/x-grub-legacy-ec2 exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-124-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-124-generic (4.4.0-124.148) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-124-generic /boot/vmlinuz-4.4.0-124-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-124-generic
run-parts: executing /etc/kernel/postrm.d/x-grub-legacy-ec2 4.4.0-124-generic /boot/vmlinuz-4.4.0-124-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
uuid not supported. update 'groot' in /boot/grub/menu.lst


groot must be grub root device (ie '(hd0)'). not 'a9a2880d-8432-4dec-a97e-a7de1c570ef3'


run-parts: /etc/kernel/postrm.d/x-grub-legacy-ec2 exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-124-generic.postrm line 330.
dpkg: error processing package linux-image-4.4.0-124-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-62-generic (4.4.0-62.83) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-62-generic
run-parts: executing /etc/kernel/postrm.d/x-grub-legacy-ec2 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
uuid not supported. update 'groot' in /boot/grub/menu.lst


groot must be grub root device (ie '(hd0)'). not 'a9a2880d-8432-4dec-a97e-a7de1c570ef3'


run-parts: /etc/kernel/postrm.d/x-grub-legacy-ec2 exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-62-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-62-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-93-generic (4.4.0-93.116) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-93-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
Error! Your kernel headers for kernel 4.4.0-93-generic cannot be found.
Please install the linux-headers-4.4.0-93-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-93-generic cannot be found.
Please install the linux-headers-4.4.0-93-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-93-generic
WARNING: missing /lib/modules/4.4.0-93-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-93-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
depmod: WARNING: could not open /var/tmp/mkinitramfs_k0j1ov/lib/modules/4.4.0-93-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_k0j1ov/lib/modules/4.4.0-93-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
run-parts: executing /etc/kernel/postinst.d/x-grub-legacy-ec2 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
uuid not supported. update 'groot' in /boot/grub/menu.lst


groot must be grub root device (ie '(hd0)'). not 'a9a2880d-8432-4dec-a97e-a7de1c570ef3'


run-parts: /etc/kernel/postinst.d/x-grub-legacy-ec2 exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-93-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-93-generic (4.4.0-93.116) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-93-generic
run-parts: executing /etc/kernel/postrm.d/x-grub-legacy-ec2 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
uuid not supported. update 'groot' in /boot/grub/menu.lst


groot must be grub root device (ie '(hd0)'). not 'a9a2880d-8432-4dec-a97e-a7de1c570ef3'


run-parts: /etc/kernel/postrm.d/x-grub-legacy-ec2 exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-93-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-93-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-121-generic
 linux-image-4.4.0-121-generic
 linux-image-extra-4.4.0-124-generic
 linux-image-4.4.0-124-generic
 linux-image-4.4.0-62-generic
 linux-image-extra-4.4.0-93-generic
 linux-image-4.4.0-93-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Impavidus on 2018-06-18
I might help if you told us what exact command caused that output.

Also show the output of the following commands:```
# What is scheduled for autoremoval?
apt-get autoremove --dry-run
# Which image and header packages are installed?
dpkg --list | egrep 'linux-image|linux-headers|linux-signed'
# Which packages are broken?
dpkg --list | egrep -v '^ii|^rc'
# What's present in your /boot directory?
ls /boot
# Have you reached the limit on the number of files on any partition?
df -i
# Have you reached the limit on total file size on any partition?
df -m
```That should give us an idea of what's going on.

---

