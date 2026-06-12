---
title: "i keep getting an error message after installs and removals"
date: 2012-08-14
forum: Installation &amp; Upgrades
---

### Post by walker195 on 2012-08-14
```
installArchives() failed: Selecting previously unselected package xmille.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 364102 files and directories currently installed.)
Unpacking xmille (from .../xmille_2.0-13ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for menu ...
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up xmille (2.0-13ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Processing triggers for menu ...
Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
```

---

### Post by walker195 on 2012-08-15
can someone please help me i need some software for school and i cant install without this problem fixed

---

