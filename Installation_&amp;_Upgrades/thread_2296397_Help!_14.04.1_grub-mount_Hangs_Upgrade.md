---
title: "Help! 14.04.1 grub-mount Hangs Upgrade"
date: 2015-09-25
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2015-09-25
Hello,

When I tried to perform the last upgrade, I received the following message:

```

sophie@sophie-notebook:~$ sudo apt-get upgrade
[sudo] password for sophie: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
sophie@sophie-notebook:~$ sudo dpkg --configure -a
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-28-generic
Setting up linux-image-extra-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
Generating grub configuration file ...
using custom appearance settings
Found background image: /home/sophie/Pictures/earth-rise.jpeg
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin

```

The last entry in the boot menu is my Windows 10 installation. It originally read Windows 7; but I edited the label to read Windows 10 in "grub-customizer." I ultimately had to kill grub-mount with "sudo kill -9 15573." 

Also, "grub-mount" is using 50% processor capacity and hangs. Repeated attempts to correct this do not work.

Any help appreciated.

Thanks, Hannibal

---

