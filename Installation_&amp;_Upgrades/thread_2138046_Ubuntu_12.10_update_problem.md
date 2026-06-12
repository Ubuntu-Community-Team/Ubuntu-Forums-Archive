---
title: "Ubuntu 12.10 update problem"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by blolass on 2013-04-22
This problem is bothering me for few weeks now. I think, it started doing that after i installed bumblebee.
Every time i install/update anything i get this error.
I google it but i just can't find right solution.

```

Setting up linux-image-3.5.0-25-generic (3.5.0-25.39) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.5.0-25.38 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.5.0-25.38 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-25-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.5.0-26-generic (3.5.0-26.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
Error! Your kernel headers for kernel 3.5.0-26-generic cannot be found.
Please install the linux-headers-3.5.0-26-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.5.0-26-generic cannot be found.
Please install the linux-headers-3.5.0-26-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-26-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.5.0-27-generic (3.5.0-27.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
Error! Your kernel headers for kernel 3.5.0-27-generic cannot be found.
Please install the linux-headers-3.5.0-27-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.5.0-27-generic cannot be found.
Please install the linux-headers-3.5.0-27-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-27-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-25-generic:
 linux-image-extra-3.5.0-25-generic depends on linux-image-3.5.0-25-generic; however:
  Package linux-image-3.5.0-25-generic is not configured yet.


dpkg: error processing linux-image-extra-3.5.0-25-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-26-generic:
 linux-image-extra-3.5.0-26-generic depends on linux-image-3.5.0-26-generic; however:
  Package linux-image-3.5.0-26-generic is not configured yet.


dpkg: error processing linux-image-extra-3.5.0-26-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-27-generic:
 linux-image-extra-3.5.0-27-generic depends on linux-image-3.5.0-27-generic; however:
  Package linux-image-3.5.0-27-generic is not configured yet.


dpkg: error processing linux-image-extra-3.5.0-27-generic (--confiPoro&#269;ilo apport ni bilo napisano, ker je bilo število MaxReports že doseženo
                                                              Poro&#269;ilo apport ni bilo napisano, ker je bilo število MaxReports že doseženo
                                                          Poro&#269;ilo apport ni bilo napisano, ker je bilo število MaxReports že doseženo
                                                      Poro&#269;ilo apport ni bilo napisano, ker je bilo število MaxReports že doseženo
                                                  gure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-27-generic; however:
  Package linux-image-3.5.0-27-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.5.0-27-generic; however:
  Package linux-image-extra-3.5.0-27-generic is not configured yet.


dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.5.0-25-generic
 linux-image-3.5.0-26-generic
 linux-image-3.5.0-27-generic
 linux-image-extra-3.5.0-25-generic
 linux-image-extra-3.5.0-26-generic
 linux-image-extra-3.5.0-27-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

