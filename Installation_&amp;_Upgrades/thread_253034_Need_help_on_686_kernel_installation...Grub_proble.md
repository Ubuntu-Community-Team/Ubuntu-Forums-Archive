---
title: "Need help on 686 kernel installation...Grub problem.."
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by kenweill on 2006-09-07
The kernel installed by default when i install kubuntu is 2.6.15-23-386.
I wanted to update the kernel to the latest and also instll the 686 kernel.

So i did update: linux-image-2.6.15-23-686
And install:
linux-image-2.6.15-26-386
linux-image-2.6.15-26-686
linux-image-686

Now, after reboot, im still using 2.6.15-23-386 kernel. Issuing the command "uname -r" produces "2.6.15-23-386"

I checked my /boot/grub/menu.lst, but i cant find the new kernels i have just installed.

I checked on my /boot and the "vmlinuz-2.6.15-26-386" and "vmlinuz-2.6.15-26-686" is there. But there's no file named "initrd.img-2.6.15-26-386" and "initrd.img-2.6.15-26-686.
Only "initrd.img-2.6.15-23-386".

What should I do?

---

