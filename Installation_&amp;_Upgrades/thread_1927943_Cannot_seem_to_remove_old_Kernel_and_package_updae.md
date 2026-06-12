---
title: "Cannot seem to remove old Kernel and package updae manager not working at all!"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by hybmg57 on 2012-02-19
Hi guys,

This is for Ubuntu 11.04 and I have a few problems. First of all, I cannot seem to upgrade to 11.10 for some reason any of my updates is not working.

I have realised that there are some old Kernels and tried to remove them by using 

[HTML]sudo dpkg --configure -a[/HTML]

But this seems to create error like below:


```
Setting up linux-image-2.6.38-11-generic-pae (2.6.38-11.50) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic-pae
Warning: No support for locale: en_NZ.utf8
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-11-generic-pae /boot/vmlinuz-2.6.38-11-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-11-generic-pae /boot/vmlinuz-2.6.38-11-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-11-generic-pae /boot/vmlinuz-2.6.38-11-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-11-generic-pae /boot/vmlinuz-2.6.38-11-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-13-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-13-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-11-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-11-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-10-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-10-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-8-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-8-generic-pae
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda3
/etc/grub.d/README: 2: All: not found
/etc/grub.d/README: 4: 00_*:: not found
/etc/grub.d/README: 5: 10_*:: not found
/etc/grub.d/README: 6: Syntax error: "(" unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-11-generic-pae.postinst line 1010.
dpkg: error processing linux-image-2.6.38-11-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.38-10-generic-pae (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic-pae
Warning: No support for locale: en_NZ.utf8
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic-pae /boot/vmlinuz-2.6.38-10-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic-pae /boot/vmlinuz-2.6.38-10-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic-pae /boot/vmlinuz-2.6.38-10-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic-pae /boot/vmlinuz-2.6.38-10-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-13-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-13-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-11-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-11-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-10-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-10-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-8-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-8-generic-pae
^CFailed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic-pae.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.38-13-generic-pae (2.6.38-13.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-13-generic-pae
Warning: No support for locale: en_NZ.utf8
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-13-generic-pae /boot/vmlinuz-2.6.38-13-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-13-generic-pae /boot/vmlinuz-2.6.38-13-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-13-generic-pae /boot/vmlinuz-2.6.38-13-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-13-generic-pae /boot/vmlinuz-2.6.38-13-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-13-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-13-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-11-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-11-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-10-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-10-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-8-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-8-generic-pae
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda3
/etc/grub.d/README: 2: All: not found
/etc/grub.d/README: 4: 00_*:: not found
/etc/grub.d/README: 5: 10_*:: not found
/etc/grub.d/README: 6: Syntax error: "(" unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-13-generic-pae.postinst line 1010.
dpkg: error processing linux-image-2.6.38-13-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.38-13-generic-pae; however:
  Package linux-image-2.6.38-13-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.38.13.28); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.38-11-generic-pae
 linux-image-2.6.38-10-generic-pae
 linux-image-2.6.38-13-generic-pae
 linux-image-generic-pae
 linux-generic-pae

```

Can anyone find out what the fix is for this?

---

### Post by ajgreeny on 2012-02-19
That command will not remove anything!  It is used most often when an upgrade or package installation has been interrupted in some way, and just makes sure all installed packages are fully configured.

See what shows in the status bar of synaptic package manager; you may have some broken packages that synaptic will be able to fix.

Then to remove unwanted kernels you can search for them in synaptic and remove them that way. which is the safest way to do it.  It is best to leave your current kernel plus the last version on the machine as a fall-back, in case something goes wrong with the newest.

---

