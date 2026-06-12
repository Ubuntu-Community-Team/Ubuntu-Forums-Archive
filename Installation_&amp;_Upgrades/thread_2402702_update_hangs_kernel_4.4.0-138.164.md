---
title: "update hangs kernel 4.4.0-138.164"
date: 2018-10-03
forum: Installation &amp; Upgrades
---

### Post by bb-ssmith on 2018-10-03
when running an upgrade i continue to hang at the following

$sudo dpkg --configure -a
Setting up linux-image-4.4.0-137-generic (4.4.0-137.163) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.4.0-137-generic
) points to /boot/initrd.img-4.4.0-137-generic
 (/boot/initrd.img-4.4.0-137-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-137-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.4.0-137-generic
) points to /boot/vmlinuz-4.4.0-137-generic
 (/boot/vmlinuz-4.4.0-137-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-137-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-137-generic /boot/vmlinuz-4.4.0-137-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-137-generic /boot/vmlinuz-4.4.0-137-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-137-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

---

