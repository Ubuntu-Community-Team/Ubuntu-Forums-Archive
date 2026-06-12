---
title: "Install of kernel 4.4.0.78 unusual"
date: 2017-05-17
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2017-05-17
The update to install kernel 4.4.0.78 on 16.04 LTS takes an extraordinary length of time to install.  In the details it shows that it is rebuilding all of the past initrd files.  The install isn't finished yet, so I do not know if this is related to the boot failure after installation of this kernel issue.  I tried to copy the details log from the update panel, but that does not seem to be supported.

---

### Post by deadflowr on 2017-05-17
The update is logged at /var/log/apt
the packages upgraded will show in the history.log file and the terminal output in the term.log file.
Additionally look at the dpkg log file, at /var/log/dpkg.log
hope it helps.

One more place where updates are logged is /var/log/unattended-upgrades/unattended-upgrades.log, if you have automatic updates enabled and in use.
(That's if you have the Download and Install updates feature in software and updates set. If you ran the update manually, then no updates will be logged in the unattended-upgrades log files, if that makes sense)

---

### Post by 7-webmaster on 2017-05-17
Thank you for those pointers.  I am posting this in case it is relevant to the reboot problem for 4.4.0.78.  The contents of term.log for today's update is:
```
Log started: 2017-05-17  13:05:59
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 1002538 files and directories currently installed.) 
Preparing to unpack .../login_1%3a4.2-3.1ubuntu5.3_amd64.deb ... 
Unpacking login (1:4.2-3.1ubuntu5.3) over (1:4.2-3.1ubuntu5.2) ... 
Processing triggers for man-db (2.7.5-1) ... 
Setting up login (1:4.2-3.1ubuntu5.3) ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 1002538 files and directories currently installed.) 
Preparing to unpack .../chromium-browser-l10n_58.0.3029.110-0ubuntu0.16.04.1281_all.deb ... 
Unpacking chromium-browser-l10n (58.0.3029.110-0ubuntu0.16.04.1281) over (58.0.3029.96-0ubuntu0.16.04.1279) ... 
Preparing to unpack .../chromium-browser_58.0.3029.110-0ubuntu0.16.04.1281_amd64.deb ... 
Unpacking chromium-browser (58.0.3029.110-0ubuntu0.16.04.1281) over (58.0.3029.96-0ubuntu0.16.04.1279) ... 
Preparing to unpack .../chromium-codecs-ffmpeg-extra_58.0.3029.110-0ubuntu0.16.04.1281_amd64.deb ... 
Unpacking chromium-codecs-ffmpeg-extra (58.0.3029.110-0ubuntu0.16.04.1281) over (58.0.3029.96-0ubuntu0.16.04.1279) ... 
Preparing to unpack .../ubuntu-core-launcher_2.25_amd64.deb ... 
Unpacking ubuntu-core-launcher (2.25) over (2.24.1) ... 
Preparing to unpack .../archives/snapd_2.25_amd64.deb ... 
Warning: Stopping snapd.service, but it can still be activated by: 
  snapd.socket 
Unpacking snapd (2.25) over (2.24.1) ... 
Preparing to unpack .../snap-confine_2.25_amd64.deb ... 
Unpacking snap-confine (2.25) over (2.24.1) ... 
Preparing to unpack .../passwd_1%3a4.2-3.1ubuntu5.3_amd64.deb ... 
Unpacking passwd (1:4.2-3.1ubuntu5.3) over (1:4.2-3.1ubuntu5.2) ... 
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ... 
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ... 
Rebuilding /usr/share/applications/bamf-2.index... 
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ... 
Processing triggers for mime-support (3.59ubuntu1) ... 
Processing triggers for man-db (2.7.5-1) ... 
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ... 
Processing triggers for ureadahead (0.100.0-19) ... 
Setting up passwd (1:4.2-3.1ubuntu5.3) ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 1002538 files and directories currently installed.) 
Preparing to unpack .../ghostscript_9.18~dfsg~0-0ubuntu2.6_amd64.deb ... 
Unpacking ghostscript (9.18~dfsg~0-0ubuntu2.6) over (9.18~dfsg~0-0ubuntu2.4) ... 
Preparing to unpack .../ghostscript-x_9.18~dfsg~0-0ubuntu2.6_amd64.deb ... 
Unpacking ghostscript-x (9.18~dfsg~0-0ubuntu2.6) over (9.18~dfsg~0-0ubuntu2.4) ... 
Preparing to unpack .../libgs9-common_9.18~dfsg~0-0ubuntu2.6_all.deb ... 
Unpacking libgs9-common (9.18~dfsg~0-0ubuntu2.6) over (9.18~dfsg~0-0ubuntu2.4) ... 
Preparing to unpack .../libgs9_9.18~dfsg~0-0ubuntu2.6_amd64.deb ... 
Unpacking libgs9:amd64 (9.18~dfsg~0-0ubuntu2.6) over (9.18~dfsg~0-0ubuntu2.4) ... 
Selecting previously unselected package libcairo-perl. 
Preparing to unpack .../libcairo-perl_1.106-1build1_amd64.deb ... 
Unpacking libcairo-perl (1.106-1build1) ... 
Selecting previously unselected package libglib-perl. 
Preparing to unpack .../libglib-perl_3%3a1.320-2_amd64.deb ... 
Unpacking libglib-perl (3:1.320-2) ... 
Selecting previously unselected package libpango-perl. 
Preparing to unpack .../libpango-perl_1.227-1_amd64.deb ... 
Unpacking libpango-perl (1.227-1) ... 
Selecting previously unselected package libgtk2-perl. 
Preparing to unpack .../libgtk2-perl_2%3a1.2498-1_amd64.deb ... 
Unpacking libgtk2-perl (2:1.2498-1) ... 
Preparing to unpack .../linux-firmware_1.157.10_all.deb ... 
Unpacking linux-firmware (1.157.10) over (1.157.8) ... 
Selecting previously unselected package linux-image-4.4.0-78-generic. 
Preparing to unpack .../linux-image-4.4.0-78-generic_4.4.0-78.99_amd64.deb ... 
Done. 
Unpacking linux-image-4.4.0-78-generic (4.4.0-78.99) ... 
Selecting previously unselected package linux-image-extra-4.4.0-78-generic. 
Preparing to unpack .../linux-image-extra-4.4.0-78-generic_4.4.0-78.99_amd64.deb ... 
Unpacking linux-image-extra-4.4.0-78-generic (4.4.0-78.99) ... 
Preparing to unpack .../linux-generic_4.4.0.78.84_amd64.deb ... 
Unpacking linux-generic (4.4.0.78.84) over (4.4.0.77.83) ... 
Preparing to unpack .../linux-image-generic_4.4.0.78.84_amd64.deb ... 
Unpacking linux-image-generic (4.4.0.78.84) over (4.4.0.77.83) ... 
Selecting previously unselected package linux-headers-4.4.0-78. 
Preparing to unpack .../linux-headers-4.4.0-78_4.4.0-78.99_all.deb ... 
Unpacking linux-headers-4.4.0-78 (4.4.0-78.99) ... 
Selecting previously unselected package linux-headers-4.4.0-78-generic. 
Preparing to unpack .../linux-headers-4.4.0-78-generic_4.4.0-78.99_amd64.deb ... 
Unpacking linux-headers-4.4.0-78-generic (4.4.0-78.99) ... 
Preparing to unpack .../linux-headers-generic_4.4.0.78.84_amd64.deb ... 
Unpacking linux-headers-generic (4.4.0.78.84) over (4.4.0.77.83) ... 
Preparing to unpack .../linux-libc-dev_4.4.0-78.99_amd64.deb ... 
Unpacking linux-libc-dev:amd64 (4.4.0-78.99) over (4.4.0-77.98) ... 
Preparing to unpack .../thunderbird-locale-en_1%3a52.1.1+build1-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking thunderbird-locale-en (1:52.1.1+build1-0ubuntu0.16.04.1) over (1:45.8.0+build1-0ubuntu0.16.04.1) ... 
Preparing to unpack .../thunderbird_1%3a52.1.1+build1-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking thunderbird (1:52.1.1+build1-0ubuntu0.16.04.1) over (1:45.8.0+build1-0ubuntu0.16.04.1) ... 
Preparing to unpack .../thunderbird-gnome-support_1%3a52.1.1+build1-0ubuntu0.16.04.1_amd64.deb ... 
Unpacking thunderbird-gnome-support (1:52.1.1+build1-0ubuntu0.16.04.1) over (1:45.8.0+build1-0ubuntu0.16.04.1) ... 
Preparing to unpack .../thunderbird-locale-en-us_1%3a52.1.1+build1-0ubuntu0.16.04.1_all.deb ... 
Unpacking thunderbird-locale-en-us (1:52.1.1+build1-0ubuntu0.16.04.1) over (1:45.8.0+build1-0ubuntu0.16.04.1) ... 
Processing triggers for man-db (2.7.5-1) ... 
Processing triggers for libc-bin (2.23-0ubuntu7) ... 
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ... 
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ... 
Rebuilding /usr/share/applications/bamf-2.index... 
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ... 
Processing triggers for mime-support (3.59ubuntu1) ... 
Setting up chromium-codecs-ffmpeg-extra (58.0.3029.110-0ubuntu0.16.04.1281) ... 
Setting up chromium-browser (58.0.3029.110-0ubuntu0.16.04.1281) ... 
Setting up chromium-browser-l10n (58.0.3029.110-0ubuntu0.16.04.1281) ... 
Setting up snapd (2.25) ... 
Installing new version of config file /etc/apparmor.d/usr.lib.snapd.snap-confine.real ... 
Setting up ubuntu-core-launcher (2.25) ... 
Setting up snap-confine (2.25) ... 
Setting up libgs9-common (9.18~dfsg~0-0ubuntu2.6) ... 
Setting up libgs9:amd64 (9.18~dfsg~0-0ubuntu2.6) ... 
Setting up ghostscript (9.18~dfsg~0-0ubuntu2.6) ... 
Setting up ghostscript-x (9.18~dfsg~0-0ubuntu2.6) ... 
Setting up libcairo-perl (1.106-1build1) ... 
Setting up libglib-perl (3:1.320-2) ... 
Setting up libpango-perl (1.227-1) ... 
Setting up libgtk2-perl (2:1.2498-1) ... 
Setting up linux-firmware (1.157.10) ... 
update-initramfs: Generating /boot/initrd.img-4.4.0-77-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-71-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-70-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-67-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-43-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic 
^A  update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-28-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-24-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-21-generic 
update-initramfs: Generating /boot/initrd.img-4.2.0-35-generic 
update-initramfs: Generating /boot/initrd.img-3.19.0-39-generic 
Setting up linux-image-4.4.0-78-generic (4.4.0-78.99) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
Generating grub configuration file ... 
Found linux image: /boot/vmlinuz-4.4.0-78-generic 
Found initrd image: /boot/initrd.img-4.4.0-78-generic 
Found linux image: /boot/vmlinuz-4.4.0-77-generic 
Found initrd image: /boot/initrd.img-4.4.0-77-generic 
Found linux image: /boot/vmlinuz-4.4.0-72-generic 
Found initrd image: /boot/initrd.img-4.4.0-72-generic 
Found linux image: /boot/vmlinuz-4.4.0-71-generic 
Found initrd image: /boot/initrd.img-4.4.0-71-generic 
Found linux image: /boot/vmlinuz-4.4.0-70-generic 
Found initrd image: /boot/initrd.img-4.4.0-70-generic 
Found linux image: /boot/vmlinuz-4.4.0-67-generic 
Found initrd image: /boot/initrd.img-4.4.0-67-generic 
Found linux image: /boot/vmlinuz-4.4.0-66-generic 
Found initrd image: /boot/initrd.img-4.4.0-66-generic 
Found linux image: /boot/vmlinuz-4.4.0-64-generic 
Found initrd image: /boot/initrd.img-4.4.0-64-generic 
Found linux image: /boot/vmlinuz-4.4.0-63-generic 
Found initrd image: /boot/initrd.img-4.4.0-63-generic 
Found linux image: /boot/vmlinuz-4.4.0-62-generic 
Found initrd image: /boot/initrd.img-4.4.0-62-generic 
Found linux image: /boot/vmlinuz-4.4.0-59-generic 
Found initrd image: /boot/initrd.img-4.4.0-59-generic 
Found linux image: /boot/vmlinuz-4.4.0-57-generic 
Found initrd image: /boot/initrd.img-4.4.0-57-generic 
Found linux image: /boot/vmlinuz-4.4.0-53-generic 
Found initrd image: /boot/initrd.img-4.4.0-53-generic 
Found linux image: /boot/vmlinuz-4.4.0-51-generic 
Found initrd image: /boot/initrd.img-4.4.0-51-generic 
Found linux image: /boot/vmlinuz-4.4.0-47-generic 
Found initrd image: /boot/initrd.img-4.4.0-47-generic 
Found linux image: /boot/vmlinuz-4.4.0-45-generic 
Found initrd image: /boot/initrd.img-4.4.0-45-generic 
Found linux image: /boot/vmlinuz-4.4.0-43-generic 
Found initrd image: /boot/initrd.img-4.4.0-43-generic 
Found linux image: /boot/vmlinuz-4.4.0-42-generic 
Found initrd image: /boot/initrd.img-4.4.0-42-generic 
Found linux image: /boot/vmlinuz-4.4.0-38-generic 
Found initrd image: /boot/initrd.img-4.4.0-38-generic 
Found linux image: /boot/vmlinuz-4.4.0-36-generic 
Found initrd image: /boot/initrd.img-4.4.0-36-generic 
Found linux image: /boot/vmlinuz-4.4.0-34-generic 
Found initrd image: /boot/initrd.img-4.4.0-34-generic 
Found linux image: /boot/vmlinuz-4.4.0-31-generic 
Found initrd image: /boot/initrd.img-4.4.0-31-generic 
Found linux image: /boot/vmlinuz-4.4.0-28-generic 
Found initrd image: /boot/initrd.img-4.4.0-28-generic 
Found linux image: /boot/vmlinuz-4.4.0-24-generic 
Found initrd image: /boot/initrd.img-4.4.0-24-generic 
Found linux image: /boot/vmlinuz-4.4.0-22-generic 
Found initrd image: /boot/initrd.img-4.4.0-22-generic 
Found linux image: /boot/vmlinuz-4.4.0-21-generic 
Found initrd image: /boot/initrd.img-4.4.0-21-generic 
Found linux image: /boot/vmlinuz-4.2.0-35-generic 
Found initrd image: /boot/initrd.img-4.2.0-35-generic 
Found linux image: /boot/vmlinuz-3.19.0-39-generic 
Found initrd image: /boot/initrd.img-3.19.0-39-generic 
Found linux image: /boot/vmlinuz-3.16.0-28-generic 
Found initrd image: /boot/initrd.img-3.16.0-28-generic 
Found linux image: /boot/vmlinuz-3.16.0-25-generic 
Found initrd image: /boot/initrd.img-3.16.0-25-generic 
Found linux image: /boot/vmlinuz-3.16.0-24-generic 
Found initrd image: /boot/initrd.img-3.16.0-24-generic 
Found linux image: /boot/vmlinuz-3.16.0-23-generic 
Found initrd image: /boot/initrd.img-3.16.0-23-generic 
Found linux image: /boot/vmlinuz-3.13.0-39-generic 
Found initrd image: /boot/initrd.img-3.13.0-39-generic 
Found linux image: /boot/vmlinuz-3.13.0-24-generic 
Found initrd image: /boot/initrd.img-3.13.0-24-generic 
Found linux image: /boot/vmlinuz-3.11.0-19-generic 
Found initrd image: /boot/initrd.img-3.11.0-19-generic 
Found memtest86+ image: /boot/memtest86+.elf 
Found memtest86+ image: /boot/memtest86+.bin 
Found Windows 7 (loader) on /dev/sda2 
Found Windows 7 (loader) on /dev/sda3 
done 
Setting up linux-image-extra-4.4.0-78-generic (4.4.0-78.99) ... 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
update-initramfs: Generating /boot/initrd.img-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
Generating grub configuration file ... 
Found linux image: /boot/vmlinuz-4.4.0-78-generic 
Found initrd image: /boot/initrd.img-4.4.0-78-generic 
Found linux image: /boot/vmlinuz-4.4.0-77-generic 
Found initrd image: /boot/initrd.img-4.4.0-77-generic 
Found linux image: /boot/vmlinuz-4.4.0-72-generic 
Found initrd image: /boot/initrd.img-4.4.0-72-generic 
Found linux image: /boot/vmlinuz-4.4.0-71-generic 
Found initrd image: /boot/initrd.img-4.4.0-71-generic 
Found linux image: /boot/vmlinuz-4.4.0-70-generic 
Found initrd image: /boot/initrd.img-4.4.0-70-generic 
Found linux image: /boot/vmlinuz-4.4.0-67-generic 
Found initrd image: /boot/initrd.img-4.4.0-67-generic 
Found linux image: /boot/vmlinuz-4.4.0-66-generic 
Found initrd image: /boot/initrd.img-4.4.0-66-generic 
Found linux image: /boot/vmlinuz-4.4.0-64-generic 
Found initrd image: /boot/initrd.img-4.4.0-64-generic 
Found linux image: /boot/vmlinuz-4.4.0-63-generic 
Found initrd image: /boot/initrd.img-4.4.0-63-generic 
Found linux image: /boot/vmlinuz-4.4.0-62-generic 
Found initrd image: /boot/initrd.img-4.4.0-62-generic 
Found linux image: /boot/vmlinuz-4.4.0-59-generic 
Found initrd image: /boot/initrd.img-4.4.0-59-generic 
Found linux image: /boot/vmlinuz-4.4.0-57-generic 
Found initrd image: /boot/initrd.img-4.4.0-57-generic 
Found linux image: /boot/vmlinuz-4.4.0-53-generic 
Found initrd image: /boot/initrd.img-4.4.0-53-generic 
Found linux image: /boot/vmlinuz-4.4.0-51-generic 
Found initrd image: /boot/initrd.img-4.4.0-51-generic 
Found linux image: /boot/vmlinuz-4.4.0-47-generic 
Found initrd image: /boot/initrd.img-4.4.0-47-generic 
Found linux image: /boot/vmlinuz-4.4.0-45-generic 
Found initrd image: /boot/initrd.img-4.4.0-45-generic 
Found linux image: /boot/vmlinuz-4.4.0-43-generic 
Found initrd image: /boot/initrd.img-4.4.0-43-generic 
Found linux image: /boot/vmlinuz-4.4.0-42-generic 
Found initrd image: /boot/initrd.img-4.4.0-42-generic 
Found linux image: /boot/vmlinuz-4.4.0-38-generic 
Found initrd image: /boot/initrd.img-4.4.0-38-generic 
Found linux image: /boot/vmlinuz-4.4.0-36-generic 
Found initrd image: /boot/initrd.img-4.4.0-36-generic 
Found linux image: /boot/vmlinuz-4.4.0-34-generic 
Found initrd image: /boot/initrd.img-4.4.0-34-generic 
Found linux image: /boot/vmlinuz-4.4.0-31-generic 
Found initrd image: /boot/initrd.img-4.4.0-31-generic 
Found linux image: /boot/vmlinuz-4.4.0-28-generic 
Found initrd image: /boot/initrd.img-4.4.0-28-generic 
Found linux image: /boot/vmlinuz-4.4.0-24-generic 
Found initrd image: /boot/initrd.img-4.4.0-24-generic 
Found linux image: /boot/vmlinuz-4.4.0-22-generic 
Found initrd image: /boot/initrd.img-4.4.0-22-generic 
Found linux image: /boot/vmlinuz-4.4.0-21-generic 
Found initrd image: /boot/initrd.img-4.4.0-21-generic 
Found linux image: /boot/vmlinuz-4.2.0-35-generic 
Found initrd image: /boot/initrd.img-4.2.0-35-generic 
Found linux image: /boot/vmlinuz-3.19.0-39-generic 
Found initrd image: /boot/initrd.img-3.19.0-39-generic 
Found linux image: /boot/vmlinuz-3.16.0-28-generic 
Found initrd image: /boot/initrd.img-3.16.0-28-generic 
Found linux image: /boot/vmlinuz-3.16.0-25-generic 
Found initrd image: /boot/initrd.img-3.16.0-25-generic 
Found linux image: /boot/vmlinuz-3.16.0-24-generic 
Found initrd image: /boot/initrd.img-3.16.0-24-generic 
Found linux image: /boot/vmlinuz-3.16.0-23-generic 
Found initrd image: /boot/initrd.img-3.16.0-23-generic 
Found linux image: /boot/vmlinuz-3.13.0-39-generic 
Found initrd image: /boot/initrd.img-3.13.0-39-generic 
Found linux image: /boot/vmlinuz-3.13.0-24-generic 
Found initrd image: /boot/initrd.img-3.13.0-24-generic 
Found linux image: /boot/vmlinuz-3.11.0-19-generic 
Found initrd image: /boot/initrd.img-3.11.0-19-generic 
Found memtest86+ image: /boot/memtest86+.elf 
Found memtest86+ image: /boot/memtest86+.bin 
Found Windows 7 (loader) on /dev/sda2 
Found Windows 7 (loader) on /dev/sda3 
done 
Setting up linux-image-generic (4.4.0.78.84) ... 
Setting up linux-headers-4.4.0-78 (4.4.0-78.99) ... 
Setting up linux-headers-4.4.0-78-generic (4.4.0-78.99) ... 
Examining /etc/kernel/header_postinst.d. 
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic 
Setting up linux-headers-generic (4.4.0.78.84) ... 
Setting up linux-generic (4.4.0.78.84) ... 
Setting up linux-libc-dev:amd64 (4.4.0-78.99) ... 
Setting up thunderbird (1:52.1.1+build1-0ubuntu0.16.04.1) ... 
Setting up thunderbird-locale-en (1:52.1.1+build1-0ubuntu0.16.04.1) ... 
Setting up thunderbird-gnome-support (1:52.1.1+build1-0ubuntu0.16.04.1) ... 
Setting up thunderbird-locale-en-us (1:52.1.1+build1-0ubuntu0.16.04.1) ... 
Processing triggers for libc-bin (2.23-0ubuntu7) ... 
Log ended: 2017-05-17  13:40:02
```

---

### Post by howefield on 2017-05-17
With that many kernels you might want to check that you have some space left in /boot. You might want to do some remedial work before it gets to a problem.

---

### Post by deadflowr on 2017-05-17
That's one spicy meatball as they say.
You have quite a few older kernels, which means when you install the new kernel the grub updater needs to add it, and as it does the updater also has to re-add the older kernels.
It also seems there was an update for the linux-firmware package which caused the system to update the initramfs for each kernel as well.

I'd recommend removing all of those older kernels but the last two (-78 and -77)
see if you can do so with the simple
```
sudo apt-get -s autoremove
```
the -s will run it in simulation mode, if it runs without spewing anything you do not like, remove the -s to do for reals.

As you have a lot of kernels, this will take a long time, as every time it removes one, it updates grub. one.. at.. a.. time.

If that doesn't work to remove (not sure why it wouldn't at least remove most of them,) there are other methods to remove them, but we can get to those when and if that's needed.

Hope it helps
or makes sense
or something something

---

### Post by 7-webmaster on 2017-05-17
> **howefield said:**
> With that many kernels you might want to check that you have some space left in /boot. You might want to do some remedial work before it gets to a problem.
I just did the recommended automatic cleanup for kernels.  Then I used the Ubuntu Tweak Janitor which found one 3.19 kernel to clean up.  That left a seven 3.11 through 3.16 kernels that apparently apt had forgotten about, so I manually deleted those and manually updated the grub2 menu, which now includes only 4.4.0-77 and 4.4.0-78 (plus the originally installed Windoze).  That cleaned up about 9GB of space.  Crossing my fingers that it will now reboot.

---

### Post by ian-weisser on 2017-05-17
Discovering old kernels that apt 'forgot' about is a bad symptom of unfixed past trauma...and potential future breakage.
Boot failure is a symptom of (perhaps different) present trauma.
Both seem to indicate perhaps a lack of basic maintenance. You must occasionally put air in the tires, or it won't go.
As a backup plan, I gently suggest having a backup plan for when your system dies unexpectedly.

---

### Post by ajgreeny on 2017-05-17
I think you must have upgraded your system from 14.04 to 16.04 at some point and did not remove the mass of kernels that were already installed before doing so.

Those old kernels, in your case the 3.11, 3.13, 3.16 and 3.19 series will not normally be removed by the autoremove command and may need to be cleaned up with dpkg commands, so to be totally sure of the current situation please show us the output of terminal command ```
dpkg -l linux-image* linux-headers*
```

---

### Post by 7-webmaster on 2017-05-23
> **ajgreeny said:**
> I think you must have upgraded your system from 14.04 to 16.04 at some point and did not remove the mass of kernels that were already installed before doing so.

Those old kernels, in your case the 3.11, 3.13, 3.16 and 3.19 series will not normally be removed by the autoremove command and may need to be cleaned up with dpkg commands, so to be totally sure of the current situation please show us the output of terminal command ```
dpkg -l linux-image* linux-headers*
```

dpkg -l linux-image* linux-headers*
dpkg-query: no packages found matching linux-image-3.18.0-031800rc5-generic_3.18.0-031800rc5.201411162035_amd64.deb
dpkg-query: no packages found matching linux-headers-3.18.0-031800rc5_3.18.0-031800rc5.201411162035_all.deb
dpkg-query: no packages found matching linux-headers-3.18.0-031800rc5-generic_3.18.0-031800rc5.201411162035_amd64.deb

How do I clean up those three anomalous debs?  I tried apt-get autoremove and apt-get clean.  I can find instructions on uninstalling a package, but these packages are not installed.

---

