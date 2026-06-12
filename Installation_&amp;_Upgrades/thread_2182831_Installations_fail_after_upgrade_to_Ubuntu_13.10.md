---
title: "Installations fail after upgrade to Ubuntu 13.10"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by David_Dahan on 2013-10-22
Hello. My laptop is hanging whenever i try to install or uninstall a program the terminal gives me the same error every time!! Please help me!
I have a HP Pavillion G6 series 
fresh upgrade from 13.04 with the sudo do-release-upgrade command

[ATTACH=CONFIG]247158[/ATTACH]

---

### Post by ian-weisser on 2013-10-22
Please show us the ENTIRE failed session. We need to see the error that caused the cascade of failures.
Use SHIFT+CTRL+C to copy highlighted text from the terminal.
Paste it here inside [CODE] tags to make it readable.

---

### Post by David_Dahan on 2013-10-23
```

david@Ubuntu-Laptop:~$ sudo apt-get upgrade
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
11 not fully installed or removed.
Need to get 0 B/170 kB of archives.
After this operation, 4,096 B disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 270891 files and directories currently installed.)
Preparing to replace ubuntu-release-upgrader-gtk 1:0.205 (using .../ubuntu-release-upgrader-gtk_1%3a0.205.1_all.deb) ...
Unpacking replacement ubuntu-release-upgrader-gtk ...
Preparing to replace ubuntu-release-upgrader-core 1:0.205 (using .../ubuntu-release-upgrader-core_1%3a0.205.1_all.deb) ...
Unpacking replacement ubuntu-release-upgrader-core ...
Preparing to replace python3-distupgrade 1:0.205 (using .../python3-distupgrade_1%3a0.205.1_all.deb) ...
Unpacking replacement python3-distupgrade ...
Processing triggers for man-db ...
Setting up linux-image-3.11.0-12-generic (3.11.0-12.19) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-12-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-19-generic...
P: Writing config for /boot/vmlinuz-3.11.0-12-generic...
P: Writing config for Windows 8 (loader) on /dev/sda1...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
/etc/grub.d/10_os-prober_proxy: 3: /etc/grub.d/10_os-prober_proxy: /etc/grub.d/proxifiedScripts/os-prober: not found
/etc/grub.d/10_os-prober_proxy: 3: /etc/grub.d/10_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-12-generic.postinst line 1010.
dpkg: error processing linux-image-3.11.0-12-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.8.0-31-generic (3.8.0-31.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-19-generic...
P: Writing config for /boot/vmlinuz-3.11.0-12-generic...
P: Writing config for Windows 8 (loader) on /dev/sda1...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
/etc/grub.d/10_os-prober_proxy: 3: /etc/grub.d/10_os-prober_proxy: /etc/grub.d/10_os-prober_proxy: 3: /etc/grub.d/10_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: not found
/etc/grub.d/proxifiedScripts/os-prober: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-31-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up memtest86+ (4.20-1.1ubuntu5) ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
/etc/grub.d/10_os-prober_proxy: 3: /etc/grub.d/10_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: not found
/etc/grub.d/10_os-prober_proxy: 3: /etc/grub.d/10_os-prober_proxy: /etc/grub.d/proxifiedScripts/os-prober: not found
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.


dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (2.00-19ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
/etc/grub.d/10_os-prober_proxy: 3: /etc/grub.d/10_os-prober_proxy: /etc/grub.d/proxifiedScripts/os-prober: not found
/etc/grub.d/10_os-prober_proxy: 3: /etc/grub.d/10_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.11.0-12-generic:
 linux-image-extra-3.11.0-12-generic depends on linux-image-3.11.0-12-generic; however:
  Package linux-image-3.11.0-12-generic is not configured yet.


dpkg: error processing linux-image-extra-3.11.0-12-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.11.0-12-generic; however:
  Package linux-image-3.11.0-12-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.11.0-12-generic; however:
  Package linux-image-extra-3.11.0-12-generic is not configured yet.


dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.11.0.12.13); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-31-generic:
 linux-image-extra-3.8.0-31-generic depends on linux-image-3.8.0-31-generic; however:
  Package linux-image-3.8.0-31-generic is not configured yet.


dpkg: error processing linux-image-extra-3.8.0-31-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of syslinux-themes-debian-wheezy:
 syslinux-themes-debian-wheezy depends on memtest86+; however:
  Package memtest86+ is not configured yet.


dpkg: error processing syslinux-themes-debian-wheezy (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of syslinux-themes-debian:
 syslinux-themes-debian depends on syslinux-themes-debian-wheezy; however:
  Package syslinux-themes-debian-wheezy is not configured yet.


dpkg: error processing syslinux-themes-debian (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up python3-distupgrade (1:0.205.1) ...
Setting up ubuntu-release-upgrader-core (1:0.205.1) ...
Setting up ubuntu-release-upgrader-gtk (1:0.205.1) ...
Errors were encountered while processing:
 linux-image-3.11.0-12-generic
 linux-image-3.8.0-31-generic
 memtest86+
 ubuntu-standard
 grub-pc
 linux-image-extra-3.11.0-12-generic
 linux-image-generic
 linux-generic
 linux-image-extra-3.8.0-31-generic
 syslinux-themes-debian-wheezy
 syslinux-themes-debian
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

