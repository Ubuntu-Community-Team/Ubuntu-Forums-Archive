---
title: "Ubuntu 14.04 LTS Kernel Errot"
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by greenfrog42 on 2014-12-13
Software Updater keeps trying to install new Linux kernel, but get these errrors? Help, thanks in advance.


Setting up linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.13.0-43-generic
) points to /boot/initrd.img-3.13.0-43-generic
 (/boot/initrd.img-3.13.0-43-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-43-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.13.0-43-generic
) points to /boot/vmlinuz-3.13.0-43-generic
 (/boot/vmlinuz-3.13.0-43-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-43-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-43-generic...
P: Writing config for Windows 7 (loader) on /dev/sda1...
P: Writing config for Windows Recovery Environment (loader) on /dev/sda2...
P: Installing debian theme...cp: cannot stat ‘/usr/share/syslinux/themes/debian-wheezy/extlinux/memtest.bin’: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-43-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not cNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                No apport report written because the error message indicates its a followup error from a previous failure.
          No apport report written because MaxReports is reached already
                                                                        onfigured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by schragge on 2014-12-13
Is the package *syslinux-themes-debian-wheezy* installed? Did you get those error messages on upgrade from an earlier release to 14.04 LTS? I'm not sure Ubuntu supports distribution upgrades with extlinux as bootloader, you would be safer by installing grub before upgrade.

---

### Post by greenfrog42 on 2014-12-13
[I]syslinux-themes-debian-wheezy was the problem, removed it and everything upgraded.

thanks for the accurate reply, have good day
[/I]

---

