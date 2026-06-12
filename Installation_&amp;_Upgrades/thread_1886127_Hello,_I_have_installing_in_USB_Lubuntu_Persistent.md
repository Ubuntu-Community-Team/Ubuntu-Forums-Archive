---
title: "Hello, I have installing in USB Lubuntu Persistent..."
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by spi_ on 2011-11-24
[FONT=Fixedsys][SIZE=3]Hello, I have installing in USB Lubuntu Persistent, why I see this message while all updates updated successfully?  And the second questions how can(only) I write Greek characters? And why cannot mount my Windows hard disk? 
[/SIZE][/FONT]
[B][FONT=Arial Black][SIZE=1]installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "el_GR.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "el_GR.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "el_GR.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 
Preparing to replace libv4l-0 0.8.5-3ubuntu1 (using .../libv4l-0_0.8.5-3ubuntu2_i386.deb) ...
Unpacking replacement libv4l-0 ...
Preparing to replace ubiquity-casper 1.287 (using .../ubiquity-casper_1.287.1_all.deb) ...
Unpacking replacement ubiquity-casper ...
Preparing to replace casper 1.287 (using .../casper_1.287.1_i386.deb) ...
Unpacking replacement casper ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Processing triggers for ureadahead ...
Setting up linux-image-3.0.0-13-generic (3.0.0-13.22) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-13-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-13-generic; however:
  Package linux-image-3.0.0-13-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.13.15); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up libv4l-0 (0.8.5-3ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
Setting up ubiquity-casper (1.287.1) ...
Setting up casper (1.287.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
Errors were encountered while processing:
 linux-image-3.0.0-13-generic
 linux-image-generic
 linux-generic
Error in function: 
Setting up linux-image-3.0.0-13-generic (3.0.0-13.22) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-13-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-13-generic; however:
  Package linux-image-3.0.0-13-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):[/SIZE][/FONT][/B]

---

