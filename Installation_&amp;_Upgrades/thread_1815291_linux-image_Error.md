---
title: "linux-image Error"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by F.R Mostert on 2011-07-31
Hi,

I Have this error after some updates How can I fix this.


reimerd@reimerd-Dell-System-XPS-L502X:~$ sudo dpkg --configure -a
[sudo] password for reimerd: 
Setting up linux-image-2.6.38-10-virtual (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-virtual
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-virtual /boot/vmlinuz-2.6.38-10-virtual
 * dkms: running auto installation service for kernel 2.6.38-10-virtual         
 *       nvidia-current (275.19)...                                      [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-virtual /boot/vmlinuz-2.6.38-10-virtual
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-virtual /boot/vmlinuz-2.6.38-10-virtual
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-virtual /boot/vmlinuz-2.6.38-10-virtual
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-virtual /boot/vmlinuz-2.6.38-10-virtual
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-virtual /boot/vmlinuz-2.6.38-10-virtual
/etc/default/grub: 25: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-virtual.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-virtual (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.38-10-virtual
reimerd@reimerd-Dell-System-XPS-L502X:~$ 

Reimerd:P:confused:

---

### Post by dino99 on 2011-07-31
why are you using this "virtual" kernel ? install an other one.

---

