---
title: "Update error"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by bhoopal on 2012-08-15
```
installArchives() failed: Setting up linux-image-3.2.0-27-generic (3.2.0-27.43) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-27-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Setting up grub-pc (1.99-21ubuntu3.1) ...
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-27-generic; however:
  Package linux-image-3.2.0-27-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.27.29); however:No apport report written because MaxReports is reached already

  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 linux-image-3.2.0-27-generic
 linux-image-3.2.0-29-generic
 grub-pc
 linux-image-generic
 linux-generic
Error in function: 
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (1.99-21ubuntu3.1) ...
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-3.2.0-27-generic (3.2.0-27.43) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
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

```

hi guys. Im getting this error in update manager after updating my laptop hp dv6 core i5 ,ati radeon hd5650,4gb ram... with ubuntu 12.04 64 bit. It says package operation failed, at the details are posted above. the 2 updates are 
1) complete generic Linux kernel (2kb)
2) Generic linux kernel image (3kb) 

what should i do?

---

### Post by bhoopal on 2012-08-15
hi guys. Im getting this error in update manager after updating my laptop hp dv6 core i5 ,ati radeon hd5650,4gb ram... with ubuntu 12.04 64 bit. It says package operation failed, at the details are posted above. the 2 updates are 
1) complete generic Linux kernel (2kb)
2) Generic linux kernel image    (3kb)  

what should i do?

---

### Post by bhoopal on 2012-08-16
please help me out. also, now when i install a program in software centre it gives me an error report, but in fact the app is installed. can the updates be undone?

---

