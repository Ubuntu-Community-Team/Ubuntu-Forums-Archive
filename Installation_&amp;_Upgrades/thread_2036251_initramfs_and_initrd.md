---
title: "initramfs and initrd"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by sopko on 2012-08-01
I understand initramfs is supposed to replace initrd  files. By default our 12.04 systems only have  /boot/initrd.img files. I have one 12.04 system that has both /boot/initrd.img and initramfs files. When removing old kernels the initrd.img files get removed but not the initramfs files.

What controls if the system generates initramfs or initrd files?

For example the odd system has both:

/boot/initramfs-3.2.0-27-generic.img
/boot/initrd.img-3.2.0-27-generic

When I removed the following old kernel packages with "apt-get -y purge"

linux-headers-3.2.0-24
linux-headers-3.2.0-24-generic
linux-image-3.2.0-24-generic

It removed

/boot/initrd.img-3.2.0-24-generic

but did not remove:

/boot/initramfs-3.2.0-24-generic.img

I needed to remove them because /boot was filling up with old kernels. Thanks for any insight.

---

### Post by Ravi5kumar on 2012-08-01
I always used Ubuntu tweak (a third party app) [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) to remove those old kernels..

---

### Post by sopko on 2012-08-02
I am trying to figure out what 12.04 is supposed to use, initrd or initramfs. I thought initramfs was the latest preferred method. We have many machines all but one is using the old initrd method on boot. I am trying to figure out what controls which method is used. I would think this is done when the kernel is installed or upgraded as part of the post install program the kernel package would run. We have both server and desktop 12.04 systems.

Can others check /boot and see if you have initrd* or initramfs* files in 12.04? Thanks.

---

