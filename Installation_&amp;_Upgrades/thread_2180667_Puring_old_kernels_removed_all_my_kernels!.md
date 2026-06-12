---
title: "Puring old kernels removed all my kernels!"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by wmdvanzyl on 2013-10-14
I know what you're thinking and no, i didn't type the command incorrectly. :)

My current kernel version was 

```
3.5.0-41-generic
```

And the command i ran was:

```
sudo apt-get remove --purge 3.5.0-2*
```

And it removed everything. I have copied and pasted as much as i could get out of the terminal here below. I want to know, how do i reinstall the needed current kernel?

```
Note, selecting 'linux-headers-3.5.0-21' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-22' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-23' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-18' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-24' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-19' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-30' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-25' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-31' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-26' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-32' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-27' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-28' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-34' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-40' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-41' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-36' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-37' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-39' for regex '3.5.0-2*'
Note, selecting 'linux-signed-image-3.5.0-34-generic' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-28-generic' for regex '3.5.0-2*'
Note, selecting 'linux-image-3.5.0-28-generic' for regex '3.5.0-2*'
Note, selecting 'linux-signed-image-3.5.0-21-generic' for regex '3.5.0-2*'
Note, selecting 'linux-signed-image-3.5.0-37-generic' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-41-generic' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-36-generic' for regex '3.5.0-2*'
Note, selecting 'linux-image-3.5.0-41-generic' for regex '3.5.0-2*'
Note, selecting 'linux-image-3.5.0-36-generic' for regex '3.5.0-2*'
Note, selecting 'linux-signed-image-3.5.0-24-generic' for regex '3.5.0-2*'
Note, selecting 'linux-signed-image-3.5.0-19-generic' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-23-generic' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-18-generic' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-39-generic' for regex '3.5.0-2*'
Note, selecting 'linux-image-3.5.0-23-generic' for regex '3.5.0-2*'
Note, selecting 'linux-image-3.5.0-18-generic' for regex '3.5.0-2*'
Note, selecting 'linux-image-3.5.0-39-generic' for regex '3.5.0-2*'
Note, selecting 'linux-signed-image-3.5.0-32-generic' for regex '3.5.0-2*'
Note, selecting 'linux-signed-image-3.5.0-27-generic' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-31-generic' for regex '3.5.0-2*'
Note, selecting 'linux-headers-3.5.0-26-generic' for regex '3.5.0-2*'
Package linux-headers-3.5.0-18 is not installed, so not removed
Package linux-headers-3.5.0-18-generic is not installed, so not removed
Package linux-headers-3.5.0-19 is not installed, so not removed
Package linux-headers-3.5.0-19-generic is not installed, so not removed
Package linux-headers-3.5.0-21 is not installed, so not removed
Package linux-headers-3.5.0-21-generic is not installed, so not removed
Package linux-headers-3.5.0-22 is not installed, so not removed
Package linux-headers-3.5.0-22-generic is not installed, so not removed
Package linux-headers-3.5.0-24 is not installed, so not removed
Package linux-headers-3.5.0-24-generic is not installed, so not removed
Package linux-headers-3.5.0-25 is not installed, so not removed
Package linux-headers-3.5.0-25-generic is not installed, so not removed
Package linux-headers-3.5.0-26 is not installed, so not removed
Package linux-headers-3.5.0-26-generic is not installed, so not removed
Package linux-headers-3.5.0-27 is not installed, so not removed
Package linux-headers-3.5.0-27-generic is not installed, so not removed
Package linux-image-3.5.0-18-generic is not installed, so not removed
Package linux-image-3.5.0-19-generic is not installed, so not removed
Package linux-image-3.5.0-21-generic is not installed, so not removed
Package linux-image-3.5.0-22-generic is not installed, so not removed
Package linux-image-3.5.0-24-generic is not installed, so not removed
Package linux-image-3.5.0-25-generic is not installed, so not removed
Package linux-image-3.5.0-26-generic is not installed, so not removed
Package linux-image-3.5.0-27-generic is not installed, so not removed
Package linux-tools-3.5.0-23 is not installed, so not removed
Package linux-tools-3.5.0-24 is not installed, so not removed
Package linux-tools-3.5.0-25 is not installed, so not removed
Package linux-tools-3.5.0-26 is not installed, so not removed
Package linux-tools-3.5.0-27 is not installed, so not removed
Package linux-tools-3.5.0-28 is not installed, so not removed
Package linux-tools-3.5.0-30 is not installed, so not removed
Package linux-tools-3.5.0-31 is not installed, so not removed
Package linux-tools-3.5.0-32 is not installed, so not removed
Package linux-tools-3.5.0-34 is not installed, so not removed
Package linux-tools-3.5.0-36 is not installed, so not removed
Package linux-tools-3.5.0-37 is not installed, so not removed
Package linux-tools-3.5.0-39 is not installed, so not removed
Package linux-tools-3.5.0-40 is not installed, so not removed
Package linux-tools-3.5.0-41 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu gir1.2-atspi-2.0 python-virtkey python-speechd liblouis2 python-brlapi python-louis python-pyatspi2 liblouis-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic-lts-quantal* linux-headers-3.5.0-23* linux-headers-3.5.0-23-generic* linux-headers-3.5.0-28* linux-headers-3.5.0-28-generic* linux-headers-3.5.0-30* linux-headers-3.5.0-30-generic*
  linux-headers-3.5.0-31* linux-headers-3.5.0-31-generic* linux-headers-3.5.0-32* linux-headers-3.5.0-32-generic* linux-headers-3.5.0-34* linux-headers-3.5.0-34-generic* linux-headers-3.5.0-36*
  linux-headers-3.5.0-36-generic* linux-headers-3.5.0-37* linux-headers-3.5.0-37-generic* linux-headers-3.5.0-39* linux-headers-3.5.0-39-generic* linux-headers-3.5.0-40* linux-headers-3.5.0-40-generic*
  linux-headers-3.5.0-41* linux-headers-3.5.0-41-generic* linux-headers-generic-lts-quantal* linux-image-3.5.0-23-generic* linux-image-3.5.0-28-generic* linux-image-3.5.0-30-generic*
  linux-image-3.5.0-31-generic* linux-image-3.5.0-32-generic* linux-image-3.5.0-34-generic* linux-image-3.5.0-36-generic* linux-image-3.5.0-37-generic* linux-image-3.5.0-39-generic* linux-image-3.5.0-40-generic*
  linux-image-3.5.0-41-generic* linux-image-generic-lts-quantal*
0 upgraded, 0 newly installed, 36 to remove and 0 not upgraded.
After this operation, 2,072 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 482830 files and directories currently installed.)
Removing linux-generic-lts-quantal ...
Removing linux-headers-3.5.0-23-generic ...
Removing linux-headers-3.5.0-23 ...
Removing linux-headers-3.5.0-28-generic ...
Removing linux-headers-3.5.0-28 ...
Removing linux-headers-3.5.0-30-generic ...
Removing linux-headers-3.5.0-30 ...
Removing linux-headers-3.5.0-31-generic ...
Removing linux-headers-3.5.0-31 ...
Removing linux-headers-3.5.0-32-generic ...
Removing linux-headers-3.5.0-32 ...
Removing linux-headers-3.5.0-34-generic ...
Removing linux-headers-3.5.0-34 ...
Removing linux-headers-3.5.0-36-generic ...
Removing linux-headers-3.5.0-36 ...
Removing linux-headers-3.5.0-37-generic ...
Removing linux-headers-3.5.0-37 ...
Removing linux-headers-3.5.0-39-generic ...
Removing linux-headers-3.5.0-39 ...
Removing linux-headers-3.5.0-40-generic ...
Removing linux-headers-3.5.0-40 ...
Removing linux-headers-generic-lts-quantal ...
Removing linux-headers-3.5.0-41-generic ...
Removing linux-headers-3.5.0-41 ...
Removing linux-image-3.5.0-23-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found initrd image: /boot/initrd.img-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-36-generic
Found initrd image: /boot/initrd.img-3.5.0-36-generic
Found linux image: /boot/vmlinuz-3.5.0-34-generic
Found initrd image: /boot/initrd.img-3.5.0-34-generic
Found linux image: /boot/vmlinuz-3.5.0-32-generic
Found initrd image: /boot/initrd.img-3.5.0-32-generic
Found linux image: /boot/vmlinuz-3.5.0-31-generic
Found initrd image: /boot/initrd.img-3.5.0-31-generic
Found linux image: /boot/vmlinuz-3.5.0-30-generic
Found initrd image: /boot/initrd.img-3.5.0-30-generic
Found linux image: /boot/vmlinuz-3.5.0-28-generic
Found initrd image: /boot/initrd.img-3.5.0-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.5.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
Removing linux-image-3.5.0-28-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found initrd image: /boot/initrd.img-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-36-generic
Found initrd image: /boot/initrd.img-3.5.0-36-generic
Found linux image: /boot/vmlinuz-3.5.0-34-generic
Found initrd image: /boot/initrd.img-3.5.0-34-generic
Found linux image: /boot/vmlinuz-3.5.0-32-generic
Found initrd image: /boot/initrd.img-3.5.0-32-generic
Found linux image: /boot/vmlinuz-3.5.0-31-generic
Found initrd image: /boot/initrd.img-3.5.0-31-generic
Found linux image: /boot/vmlinuz-3.5.0-30-generic
Found initrd image: /boot/initrd.img-3.5.0-30-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.5.0-28-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
Removing linux-image-3.5.0-30-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found initrd image: /boot/initrd.img-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-36-generic
Found initrd image: /boot/initrd.img-3.5.0-36-generic
Found linux image: /boot/vmlinuz-3.5.0-34-generic
Found initrd image: /boot/initrd.img-3.5.0-34-generic
Found linux image: /boot/vmlinuz-3.5.0-32-generic
Found initrd image: /boot/initrd.img-3.5.0-32-generic
Found linux image: /boot/vmlinuz-3.5.0-31-generic
Found initrd image: /boot/initrd.img-3.5.0-31-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.5.0-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic
Removing linux-image-3.5.0-31-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found initrd image: /boot/initrd.img-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-36-generic
Found initrd image: /boot/initrd.img-3.5.0-36-generic
Found linux image: /boot/vmlinuz-3.5.0-34-generic
Found initrd image: /boot/initrd.img-3.5.0-34-generic
Found linux image: /boot/vmlinuz-3.5.0-32-generic
Found initrd image: /boot/initrd.img-3.5.0-32-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.5.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-31-generic /boot/vmlinuz-3.5.0-31-generic
Removing linux-image-3.5.0-32-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found initrd image: /boot/initrd.img-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-36-generic
Found initrd image: /boot/initrd.img-3.5.0-36-generic
Found linux image: /boot/vmlinuz-3.5.0-34-generic
Found initrd image: /boot/initrd.img-3.5.0-34-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.5.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-32-generic /boot/vmlinuz-3.5.0-32-generic
Removing linux-image-3.5.0-34-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found initrd image: /boot/initrd.img-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-36-generic
Found initrd image: /boot/initrd.img-3.5.0-36-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.5.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-34-generic /boot/vmlinuz-3.5.0-34-generic
Removing linux-image-3.5.0-36-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found initrd image: /boot/initrd.img-3.5.0-37-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.5.0-36-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic
Removing linux-image-3.5.0-37-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
dkms: removing: fglrx-updates 12.104 (3.5.0-37-generic) (i686)

-------- Uninstall Beginning --------
Module:  fglrx-updates
Version: 12.104
Kernel:  3.5.0-37-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

fglrx_updates.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-37-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.5.0-37-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
Removing linux-image-3.5.0-39-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-39-generic /boot/vmlinuz-3.5.0-39-generic
dkms: removing: fglrx-updates 12.104 (3.5.0-39-generic) (i686)

-------- Uninstall Beginning --------
Module:  fglrx-updates
Version: 12.104
Kernel:  3.5.0-39-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

fglrx_updates.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-39-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-39-generic /boot/vmlinuz-3.5.0-39-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-39-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-39-generic /boot/vmlinuz-3.5.0-39-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.5.0-39-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-39-generic /boot/vmlinuz-3.5.0-39-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-39-generic /boot/vmlinuz-3.5.0-39-generic
Removing linux-image-3.5.0-40-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-40-generic /boot/vmlinuz-3.5.0-40-generic
dkms: removing: fglrx-updates 12.104 (3.5.0-40-generic) (i686)

-------- Uninstall Beginning --------
Module:  fglrx-updates
Version: 12.104
Kernel:  3.5.0-40-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

fglrx_updates.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-40-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-40-generic /boot/vmlinuz-3.5.0-40-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-40-generic /boot/vmlinuz-3.5.0-40-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.5.0-41-generic
Found initrd image: /boot/initrd.img-3.5.0-41-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.5.0-40-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-40-generic /boot/vmlinuz-3.5.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-40-generic /boot/vmlinuz-3.5.0-40-generic
Removing linux-image-generic-lts-quantal ...
Removing linux-image-3.5.0-41-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-41-generic /boot/vmlinuz-3.5.0-41-generic
dkms: removing: fglrx-updates 12.104 (3.5.0-41-generic) (i686)

-------- Uninstall Beginning --------
Module:  fglrx-updates
Version: 12.104
Kernel:  3.5.0-41-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

fglrx_updates.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-41-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-41-generic /boot/vmlinuz-3.5.0-41-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-41-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-41-generic /boot/vmlinuz-3.5.0-41-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.5.0-41-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-41-generic /boot/vmlinuz-3.5.0-41-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-41-generic /boot/vmlinuz-3.5.0-41-generic
willie@gambit:~$ sudo update-grub
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
willie@gambit:~$ ls /boot
grub  memtest86+.bin  memtest86+_multiboot.bin
willie@gambit:~$ 


```

**_UPDATE:_ I have installed "linux-generic" using the Ubuntu Software Centre and ran update-grub. Will this be sufficient?**

---

### Post by fantab on 2013-10-14
Install Linux:
```
sudo apt-get install linux
```

This will install the entire linux metapackage. If anything is missing then this should take care of it.

Next time you want to remove un-needed kernels use the following:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut  -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
```
This is a dry run. Check carefully what kernels are going to be removed. 

If all is good run the real thing:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

---

### Post by wmdvanzyl on 2013-10-14
Thanks for this excellent reply. I have followed your advice and it seems i can still boot.

Those commands are beautiful... thanks.

---

### Post by oh my on 2013-10-14
Hi,

having done the [same mistake](http://ubuntuforums.org/showthread.php?t=1567809&p=10352427#post10352427) as you and to help you prevent this in the future:
> sudo apt-get remove --purge 3.5.0-2* 
The * here means 0 or more times the previous character, in this time the 2. So it will match anything that starts with 3.5.0-, which includes your current kernel. 

regards
oh my

---

### Post by wmdvanzyl on 2013-10-15
When you try and solve one problem with RegEx, you are left with two problems. :P

I seriously forgot about that! I just don't use regex enough and one falls into the habit or using * as a wildcard on the command line. Ugh.

Thanks all for the input. I have thoroughly destroyed this system, but i am trying to salvage it as we speak. I installed the linux kernel and set up grub, but when booting it didn't get past starting all the services. So i'm trying to upgrade to 13.04 to see if i can't "accidentally" solve some of the issues i seem to have created. If that doesn't work, i'll just start over from the backup drive. :facepalm:

---

### Post by mastablasta on 2013-10-15
it also said: *The following packages will be REMOVED*:
all your kernels listed

and: [I]Do you want to continue [Y/n]? 
[/I]
and you said y

---

### Post by wmdvanzyl on 2013-10-15
> **mastablasta said:**
> it also said: *The following packages will be REMOVED*:
all your kernels listed

and: [I]Do you want to continue [Y/n]? 
[/I]
and you said y

It SHOULD have said: Are you an idiot? 

I probably would still have answered yes... ](*,)

---

### Post by mastablasta on 2013-10-15
i am just pointing out one has to read what OS is communicatin before confirming.

which reminds me how i had this perfect install of original win98SE in the 90's and wanted to make some space on disk. i couldn't remove certian .tmp files as windows wouldn't allow it. so i decided to go hard core - boot from floppy and remove them. in your face OS!!!! well it failed to boot (i deleted some crucial system files - no wonder it didn't allow me to delete them). couldn't find the system install disk so i had to go with a pirate copy....UGH!

Perhaps we should have computer like in HAL in that movie Space oddisey - it would go "what are you doing mastalasta? stop it mastablasta! i can't allow this!" and then it would  remove oxygen from the room...

---

### Post by maybe2 on 2013-11-01
Thanks.  The dpkg statement was very helpful -- and informative.

The dry-run produced another suggestion in getting rid of obsolete packages:

apt-get autoremove

---

